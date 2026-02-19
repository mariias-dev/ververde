<script setup>
import { Calendar, ArrowRight } from 'lucide-vue-next'
</script>

<template>
  <section id="cta" class="py-24 bg-slate-50 relative overflow-hidden">
    <div class="max-w-5xl mx-auto px-6">
      <div
        v-motion
        class="relative bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900 rounded-3xl p-12 md:p-16 shadow-2xl overflow-hidden"
        :initial="{ opacity: 0, scale: 0.95 }"
        :visible-once="{ opacity: 1, scale: 1 }"
        :duration="800"
      >
        <div class="absolute top-0 right-0 w-96 h-96 bg-blue-500/20 rounded-full blur-3xl animate-cta-blob-1" />
        <div class="absolute bottom-0 left-0 w-96 h-96 bg-orange-500/20 rounded-full blur-3xl animate-cta-blob-2" />

        <div class="relative z-10 text-center">
          <div
            v-motion
            :initial="{ opacity: 0, y: 20 }"
            :visible-once="{ opacity: 1, y: 0 }"
            :duration="600"
            :delay="200"
          >
            <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
              Ready to Maximize Your
              <span class="bg-gradient-to-r from-blue-400 to-orange-400 bg-clip-text text-transparent">
                Marketing Efficiency?
              </span>
            </h2>
            <p class="text-xl text-slate-300 mb-10 max-w-2xl mx-auto leading-relaxed">
              Book a 15-minute strategy call. No fluff, no sales pitch—just a clear roadmap on how
              we can scale your business.
            </p>
          </div>

          <div
            v-motion
            :initial="{ opacity: 0, y: 20 }"
            :visible-once="{ opacity: 1, y: 0 }"
            :duration="600"
            :delay="400"
          >
            <a
              href="mailto:ververde_ltd@yahoo.com"
              class="inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-full text-lg font-medium transition-all bg-gradient-to-r from-orange-500 to-orange-600 hover:from-orange-600 hover:to-orange-700 text-white px-10 py-7 shadow-2xl shadow-orange-500/30 hover:shadow-3xl hover:shadow-orange-500/40 hover:scale-105"
            >
              <Calendar class="mr-3 w-6 h-6" />
              Book My Strategy Call
              <ArrowRight class="ml-3 w-6 h-6" />
            </a>
          </div>

          <div
            v-motion
            class="flex flex-wrap justify-center items-center gap-8 mt-12 pt-12 border-t border-slate-700"
            :initial="{ opacity: 0 }"
            :visible-once="{ opacity: 1 }"
            :duration="600"
            :delay="600"
          >
            <div v-for="item in ['15-min call', 'No commitment', 'Free roadmap', 'UK-based team']" :key="item" class="flex items-center gap-2 text-slate-300">
              <div class="w-2 h-2 rounded-full bg-green-400" />
              <span>{{ item }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
