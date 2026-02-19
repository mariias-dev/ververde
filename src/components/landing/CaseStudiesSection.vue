<script setup>
import { TrendingUp, ArrowUpRight } from 'lucide-vue-next'

const cases = [
  {
    industry: 'E-commerce Brand',
    result: 'Scaled from £5k to £50k monthly spend while maintaining a 4.5x ROAS.',
    metric: '4.5x ROAS',
    description: 'Scaled ad spend 10x while keeping performance profitable.',
    gradient: 'from-blue-500 to-cyan-500',
    stats: [
      { label: 'Ad Spend', value: '10x' },
      { label: 'ROAS', value: '4.5x' },
    ],
  },
  {
    industry: 'B2B SaaS',
    result: 'Reduced Cost Per Lead by 52% within the first 60 days of management.',
    metric: '52% CPL drop',
    description: 'Precision targeting and conversion optimization to reduce CPL fast.',
    gradient: 'from-purple-500 to-pink-500',
    stats: [
      { label: 'CPL', value: '-52%' },
      { label: 'Timeline', value: '60 days' },
    ],
  },
  {
    industry: 'Local Services',
    result: 'Generated 300+ high-quality inquiries in a competitive UK market using Google Search.',
    metric: '300+ inquiries',
    description: 'Hyper-targeted Google Search campaigns to drive consistent demand.',
    gradient: 'from-orange-500 to-red-500',
    stats: [
      { label: 'Inquiries', value: '300+' },
      { label: 'Quality', value: 'High' },
    ],
  },
]
</script>

<template>
  <section id="case-studies" class="py-24 bg-slate-900 relative overflow-hidden">
    <div class="absolute inset-0">
      <div class="absolute top-0 left-1/4 w-96 h-96 bg-blue-500/10 rounded-full blur-3xl animate-case-blob-1" />
      <div class="absolute bottom-0 right-1/4 w-96 h-96 bg-orange-500/10 rounded-full blur-3xl animate-case-blob-2" />
    </div>

    <div class="max-w-7xl mx-auto px-6 relative z-10">
      <div
        v-motion
        class="text-center mb-16"
        :initial="{ opacity: 0, y: 30 }"
        :visible-once="{ opacity: 1, y: 0 }"
        :duration="800"
      >
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-green-500/10 border border-green-500/20 text-green-400 text-sm font-medium mb-6">
          <TrendingUp class="w-4 h-4" />
          Proven Results
        </div>
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Real Results for
          <span class="bg-gradient-to-r from-blue-400 to-orange-400 bg-clip-text text-transparent">
            Real Businesses
          </span>
        </h2>
        <p class="text-xl text-slate-300 max-w-3xl mx-auto">
          Don't take our word for it—see what we've achieved for clients just like you
        </p>
      </div>

      <div class="grid md:grid-cols-3 gap-6">
        <div
          v-for="(caseStudy, index) in cases"
          :key="caseStudy.industry"
          v-motion
          class="group relative bg-slate-800/50 backdrop-blur-sm rounded-2xl p-8 border border-slate-700 hover:border-slate-600 transition-all overflow-hidden"
          :initial="{ opacity: 0, y: 30 }"
          :visible-once="{ opacity: 1, y: 0 }"
          :duration="600"
          :delay="index * 150"
          :hovered="{ scale: 1.05, y: -10 }"
        >
          <div
            class="absolute inset-0 opacity-0 group-hover:opacity-10 transition-opacity duration-300"
            :class="`bg-gradient-to-br ${caseStudy.gradient}`"
          />

          <div class="relative z-10">
            <div class="inline-block px-3 py-1 rounded-full bg-slate-700/50 text-slate-300 text-sm font-medium mb-4">
              {{ caseStudy.industry }}
            </div>

            <h3 class="text-2xl font-bold text-white mb-2 leading-tight">
              {{ caseStudy.result }}
            </h3>

            <div class="inline-flex items-center gap-2 text-xl font-bold bg-gradient-to-r bg-clip-text text-transparent mb-4" :class="caseStudy.gradient">
              {{ caseStudy.metric }}
              <ArrowUpRight class="w-5 h-5 text-green-400" />
            </div>

            <p class="text-slate-400 leading-relaxed mb-6">
              {{ caseStudy.description }}
            </p>

            <div class="flex gap-6 pt-6 border-t border-slate-700">
              <div v-for="stat in caseStudy.stats" :key="stat.label">
                <div class="text-2xl font-bold bg-gradient-to-r bg-clip-text text-transparent" :class="caseStudy.gradient">
                  {{ stat.value }}
                </div>
                <div class="text-xs text-slate-500 mt-1">{{ stat.label }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div
        v-motion
        class="text-center mt-12"
        :initial="{ opacity: 0 }"
        :visible-once="{ opacity: 1 }"
        :duration="800"
        :delay="800"
      >
        <p class="text-slate-400 text-sm">
          * Results are specific to individual client campaigns. Past performance does not guarantee future results.
        </p>
      </div>
    </div>
  </section>
</template>
