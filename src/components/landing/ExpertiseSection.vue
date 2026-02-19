<script setup>
import { Share2, Search, BarChart3, Target } from 'lucide-vue-next'

const services = [
  {
    icon: Share2,
    title: 'Paid Social',
    subtitle: 'Meta, TikTok, LinkedIn',
    description: 'We find your customers where they spend their time, using creative-led strategies that convert.',
    gradient: 'from-blue-500 to-cyan-500',
  },
  {
    icon: Search,
    title: 'Search & Display',
    subtitle: 'Google Ads, Bing',
    description: 'Capturing high-intent traffic at the exact moment they are looking for your solution.',
    gradient: 'from-orange-500 to-red-500',
  },
  {
    icon: BarChart3,
    title: 'Data & Analytics',
    subtitle: 'Full-Funnel Tracking',
    description: 'Full-funnel tracking to ensure every pound spent is accounted for and optimized.',
    gradient: 'from-purple-500 to-pink-500',
  },
  {
    icon: Target,
    title: 'Conversion Rate Optimization',
    subtitle: 'CRO',
    description: "We don't just send traffic; we help you fix your landing pages to ensure that traffic actually buys.",
    gradient: 'from-green-500 to-emerald-500',
  },
]
</script>

<template>
  <section class="py-24 bg-slate-50 relative overflow-hidden">
    <div class="max-w-7xl mx-auto px-6">
      <div
        v-motion
        class="text-center mb-16"
        :initial="{ opacity: 0, y: 30 }"
        :visible-once="{ opacity: 1, y: 0 }"
        :duration="800"
      >
        <h2 class="text-4xl md:text-5xl font-bold text-slate-900 mb-6">
          High-Performance Solutions for
          <span class="bg-gradient-to-r from-blue-600 to-orange-500 bg-clip-text text-transparent">
            Rapid Scaling
          </span>
        </h2>
        <p class="text-xl text-slate-600 max-w-3xl mx-auto">
          We deploy cutting-edge strategies across all major platforms to maximize your returns
        </p>
      </div>

      <div class="grid md:grid-cols-2 gap-6">
        <div
          v-for="(service, index) in services"
          :key="service.title"
          v-motion
          class="group relative bg-white rounded-2xl p-8 shadow-lg hover:shadow-2xl transition-all duration-300 border border-slate-200 overflow-hidden"
          :initial="{ opacity: 0, y: 30 }"
          :visible-once="{ opacity: 1, y: 0 }"
          :duration="600"
          :delay="index * 100"
          :hovered="{ scale: 1.02, y: -5 }"
        >
          <div
            class="absolute inset-0 opacity-0 group-hover:opacity-5 transition-opacity duration-300"
            :class="`bg-gradient-to-br ${service.gradient}`"
          />

          <div class="relative z-10">
            <div
              class="inline-flex w-14 h-14 rounded-xl items-center justify-center mb-6 shadow-lg"
              :class="`bg-gradient-to-br ${service.gradient}`"
            >
              <component :is="service.icon" class="w-7 h-7 text-white" />
            </div>

            <h3 class="text-2xl font-bold text-slate-900 mb-2">{{ service.title }}</h3>
            <p class="text-sm font-medium bg-gradient-to-r bg-clip-text text-transparent mb-4" :class="service.gradient">
              {{ service.subtitle }}
            </p>
            <p class="text-slate-600 leading-relaxed">{{ service.description }}</p>

            <div
              class="mt-6 inline-flex items-center text-sm font-medium bg-gradient-to-r bg-clip-text text-transparent transition-transform duration-200 group-hover:translate-x-1"
              :class="service.gradient"
            >
              Learn more →
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
