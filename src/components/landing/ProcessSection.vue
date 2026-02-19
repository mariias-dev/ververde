<script setup>
import { Search, Rocket, RefreshCw } from 'lucide-vue-next'

const steps = [
  {
    number: '01',
    icon: Search,
    title: 'Audit & Strategy',
    description: 'We dissect your current ad accounts to find "budget leaks" and define your scaling potential.',
    color: 'blue',
  },
  {
    number: '02',
    icon: Rocket,
    title: 'Execution & Testing',
    description: 'Rapid deployment of high-converting creatives and precise audience targeting.',
    color: 'orange',
  },
  {
    number: '03',
    icon: RefreshCw,
    title: 'Daily Optimization',
    description: "We don't \"set and forget.\" We monitor your campaigns daily, shifting budget to what works and cutting what doesn't.",
    color: 'green',
  },
]

const colorMap = {
  blue: {
    bg: 'bg-blue-50',
    border: 'border-blue-200',
    text: 'text-blue-600',
    gradient: 'from-blue-500 to-blue-600',
  },
  orange: {
    bg: 'bg-orange-50',
    border: 'border-orange-200',
    text: 'text-orange-600',
    gradient: 'from-orange-500 to-orange-600',
  },
  green: {
    bg: 'bg-green-50',
    border: 'border-green-200',
    text: 'text-green-600',
    gradient: 'from-green-500 to-green-600',
  },
}
</script>

<template>
  <section class="py-24 bg-white relative overflow-hidden">
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_30%_50%,rgba(59,130,246,0.05),transparent_50%)]" />

    <div class="max-w-7xl mx-auto px-6 relative z-10">
      <div
        v-motion
        class="text-center mb-16"
        :initial="{ opacity: 0, y: 30 }"
        :visible-once="{ opacity: 1, y: 0 }"
        :duration="800"
      >
        <h2 class="text-4xl md:text-5xl font-bold text-slate-900 mb-6">
          Our 3-Step
          <span class="bg-gradient-to-r from-blue-600 to-orange-500 bg-clip-text text-transparent">
            Efficiency Framework
          </span>
        </h2>
        <p class="text-xl text-slate-600 max-w-3xl mx-auto">
          A proven methodology that transforms ad spend into predictable revenue
        </p>
      </div>

      <div class="relative">
        <div class="hidden md:block absolute top-1/2 left-0 right-0 h-1 bg-gradient-to-r from-blue-200 via-orange-200 to-green-200 transform -translate-y-1/2" />

        <div class="grid md:grid-cols-3 gap-8 relative z-10">
          <div
            v-for="(step, index) in steps"
            :key="step.number"
            v-motion
            class="relative"
            :initial="{ opacity: 0, y: 40 }"
            :visible-once="{ opacity: 1, y: 0 }"
            :duration="600"
            :delay="index * 200"
            :hovered="{ y: -10 }"
          >
            <div class="bg-white rounded-2xl p-8 shadow-xl border-2 border-slate-100 hover:border-slate-200 transition-all h-full">
              <div class="absolute -top-6 left-8">
                <div class="w-12 h-12 rounded-full flex items-center justify-center shadow-lg" :class="`bg-gradient-to-br ${colorMap[step.color].gradient}`">
                  <span class="text-white font-bold text-lg">{{ step.number }}</span>
                </div>
              </div>

              <div
                class="inline-flex w-16 h-16 rounded-xl border-2 items-center justify-center mb-6 mt-8"
                :class="`${colorMap[step.color].bg} ${colorMap[step.color].border}`"
              >
                <component :is="step.icon" class="w-8 h-8" :class="colorMap[step.color].text" />
              </div>

              <h3 class="text-2xl font-bold text-slate-900 mb-4">{{ step.title }}</h3>
              <p class="text-slate-600 leading-relaxed">{{ step.description }}</p>
            </div>
          </div>
        </div>
      </div>

      <div
        v-motion
        class="text-center mt-16"
        :initial="{ opacity: 0, y: 30 }"
        :visible-once="{ opacity: 1, y: 0 }"
        :duration="800"
        :delay="800"
      >
        <p class="text-lg text-slate-600 italic">
          "Unlike other agencies, we don't disappear after setup. We're in your campaigns every single day."
        </p>
      </div>
    </div>
  </section>
</template>
