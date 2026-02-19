<script setup>
import { ArrowRight, TrendingUp, Zap } from 'lucide-vue-next'
import Button from '@/components/ui/Button.vue'

const stats = [
  { value: '4.5x', label: 'Average ROAS' },
  { value: '52%', label: 'CPL Reduction' },
  { value: '300+', label: 'Quality Leads/Month' },
]
</script>

<template>
    <section id="home" class="relative min-h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900">
    <div class="absolute inset-0 overflow-hidden">
      <div
        class="absolute top-20 left-10 w-72 h-72 bg-blue-500/10 rounded-full blur-3xl animate-hero-blob-1"
      />
      <div
        class="absolute bottom-20 right-10 w-96 h-96 bg-orange-500/10 rounded-full blur-3xl animate-hero-blob-2"
      />
    </div>

    <div
      class="absolute inset-0 bg-[linear-gradient(to_right,#80808012_1px,transparent_1px),linear-gradient(to_bottom,#80808012_1px,transparent_1px)] bg-[size:24px_24px]"
    />

    <div class="relative z-10 max-w-7xl mx-auto px-6 py-20 text-center">
      <div v-motion :initial="{ opacity: 0, y: 30 }" :enter="{ opacity: 1, y: 0 }" :duration="800">
        <div class="mb-6">
          <div class="text-xs uppercase tracking-[0.25em] text-slate-400">
            <span class="font-semibold text-slate-200 tracking-[0.35em]">VERVERDE LTD</span>
            <span class="mx-2 text-slate-600">—</span>
            UK Performance Marketing Agency
          </div>
        </div>

        <h1
          v-motion
          class="text-5xl md:text-7xl font-bold text-white mb-6 leading-tight"
          :initial="{ opacity: 0, y: 20 }"
          :enter="{ opacity: 1, y: 0 }"
          :delay="300"
          :duration="800"
        >
          Stop Wasting Your Ad Spend.
          <span class="bg-gradient-to-r from-blue-400 to-orange-400 bg-clip-text text-transparent">
            We Turn Traffic Into Tangible Revenue.
          </span>
        </h1>

        <p
          v-motion
          class="text-xl md:text-2xl text-slate-300 mb-12 max-w-4xl mx-auto leading-relaxed"
          :initial="{ opacity: 0, y: 20 }"
          :enter="{ opacity: 1, y: 0 }"
          :delay="500"
          :duration="800"
        >
          A UK-based performance agency for businesses that demand ROI. You provide the budget;
          we deploy it with surgical precision across Social & Search networks to scale your profits.
        </p>

        <div
          v-motion
          class="flex flex-col sm:flex-row gap-4 justify-center items-center"
          :initial="{ opacity: 0, y: 20 }"
          :enter="{ opacity: 1, y: 0 }"
          :delay="700"
          :duration="800"
        >
          <Button
            as="a"
            href="#cta"
            size="lg"
            class="bg-gradient-to-r from-orange-500 to-orange-600 hover:from-orange-600 hover:to-orange-700 text-white px-8 py-6 text-lg rounded-full shadow-xl shadow-orange-500/20 transition-all hover:shadow-2xl hover:shadow-orange-500/30 hover:scale-105"
          >
            Get a Free Growth Audit
            <ArrowRight class="ml-2 w-5 h-5" />
          </Button>
          <Button
            as="a"
            href="#case-studies"
            size="lg"
            variant="outline"
            class="border-2 border-slate-600 bg-slate-900/30 text-white hover:bg-slate-800 hover:text-white px-8 py-6 text-lg rounded-full transition-all hover:scale-105"
          >
            View Case Studies
            <TrendingUp class="ml-2 w-5 h-5" />
          </Button>
        </div>
      </div>

      <div
        v-motion
        class="grid grid-cols-3 gap-8 mt-20 max-w-3xl mx-auto"
        :initial="{ opacity: 0, y: 40 }"
        :enter="{ opacity: 1, y: 0 }"
        :delay="1000"
        :duration="800"
      >
        <div
          v-for="(stat, index) in stats"
          :key="index"
          v-motion
          class="text-center"
          :hovered="{ scale: 1.05 }"
        >
          <div class="text-3xl md:text-4xl font-bold bg-gradient-to-r from-blue-400 to-orange-400 bg-clip-text text-transparent">
            {{ stat.value }}
          </div>
          <div class="text-slate-400 text-sm mt-2">{{ stat.label }}</div>
        </div>
      </div>
    </div>

    <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-scroll-indicator">
      <div class="w-6 h-10 border-2 border-slate-600 rounded-full flex justify-center">
        <div class="w-1.5 h-1.5 bg-blue-400 rounded-full mt-2 animate-scroll-dot" />
      </div>
    </div>
  </section>
</template>
