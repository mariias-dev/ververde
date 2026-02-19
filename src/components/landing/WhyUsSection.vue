<script setup>
import { AlertCircle, Target, TrendingUp, Shield } from 'lucide-vue-next'
import useEmblaCarousel from 'embla-carousel-vue'
import { computed, onMounted, onUnmounted, ref } from 'vue'

const features = [
  {
    icon: Target,
    title: 'Laser-Focused on ROI',
    description: 'Every decision we make is driven by one question: Will this increase your revenue?',
  },
  {
    icon: TrendingUp,
    title: 'Data-Driven Optimization',
    description: 'Real-time analytics and daily monitoring ensure your budget works harder.',
  },
  {
    icon: Shield,
    title: 'Your Budget, Our Mission',
    description: 'We treat your advertising spend as if it were our own—with care and precision.',
  },
]

const [emblaRef, emblaApi] = useEmblaCarousel({
  align: 'start',
  loop: false,
  containScroll: 'trimSnaps',
})

const selectedIndex = ref(0)
const snapCount = ref(0)

const scrollTo = (index) => {
  if (emblaApi.value) emblaApi.value.scrollTo(index)
}

const onSelect = () => {
  if (!emblaApi.value) return
  selectedIndex.value = emblaApi.value.selectedScrollSnap()
}

const onInit = () => {
  if (!emblaApi.value) return
  snapCount.value = emblaApi.value.scrollSnapList().length
  onSelect()
}

onMounted(() => {
  if (!emblaApi.value) return
  emblaApi.value.on('init', onInit)
  emblaApi.value.on('select', onSelect)
  onInit()
})

onUnmounted(() => {
  if (!emblaApi.value) return
  emblaApi.value.off('init', onInit)
  emblaApi.value.off('select', onSelect)
})

const snaps = computed(() => Array.from({ length: snapCount.value }, (_, i) => i))
</script>

<template>
  <section id="why-us" class="py-24 bg-white relative overflow-hidden">
    <div class="absolute top-0 right-0 w-1/3 h-full bg-gradient-to-l from-blue-50 to-transparent" />

    <div class="max-w-7xl mx-auto px-3 sm:px-6 relative z-10">
      <div
        v-motion
        class="max-w-4xl mx-auto text-center mb-20"
        :initial="{ opacity: 0, y: 30 }"
        :visible-once="{ opacity: 1, y: 0 }"
        :duration="800"
      >
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-red-50 border border-red-100 text-red-600 text-sm font-medium mb-6">
          <AlertCircle class="w-4 h-4" />
          The Problem
        </div>
        <h2 class="text-4xl md:text-5xl font-bold text-slate-900 mb-6">
          Tired of Paying for "Impressions" While Your
          <span class="text-red-500">Sales Stagnate?</span>
        </h2>
        <p class="text-xl text-slate-600 leading-relaxed">
          Most agencies focus on vanity metrics—likes, clicks, and "reach." We believe if it doesn't
          improve your bottom line, it's a waste of money.
        </p>
      </div>

      <div
        v-motion
        class="bg-gradient-to-br from-slate-900 to-slate-800 rounded-none sm:rounded-3xl p-8 sm:p-12 md:p-16 shadow-2xl -mx-3 sm:mx-0"
        :initial="{ opacity: 0, y: 30 }"
        :visible-once="{ opacity: 1, y: 0 }"
        :duration="800"
        :delay="200"
      >
        <div class="text-center mb-12">
          <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-green-500/10 border border-green-500/20 text-green-400 text-sm font-medium mb-6">
            <Shield class="w-4 h-4" />
            Our Promise
          </div>
          <h3 class="text-3xl md:text-4xl font-bold text-white mb-6">
            We Treat Your Budget Like Our Own
          </h3>
          <p class="text-xl text-slate-300 max-w-3xl mx-auto leading-relaxed">
            Our strategy is simple: data-driven placement, relentless optimization, and a 100% focus
            on your Cost Per Acquisition (CPA) and ROAS.
          </p>
        </div>

        <div class="mt-12">
          <div class="whyus-embla md:hidden" ref="emblaRef">
            <div class="whyus-embla__container">
              <div
                v-for="(feature, index) in features"
                :key="feature.title"
                v-motion
                class="whyus-embla__slide bg-slate-800/50 backdrop-blur-sm rounded-2xl p-6 border border-slate-700"
                :initial="{ opacity: 0, y: 20 }"
                :visible-once="{ opacity: 1, y: 0 }"
                :duration="600"
                :delay="200 + index * 100"
              >
                <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-blue-500 to-blue-600 flex items-center justify-center mb-4">
                  <component :is="feature.icon" class="w-6 h-6 text-white" />
                </div>
                <h4 class="text-xl font-bold text-white mb-3">{{ feature.title }}</h4>
                <p class="text-slate-400 leading-relaxed">{{ feature.description }}</p>
              </div>
            </div>
          </div>

          <div class="whyus-embla__dots md:hidden">
            <button
              v-for="dot in snaps"
              :key="dot"
              type="button"
              class="whyus-embla__dot"
              :class="{ 'is-active': selectedIndex === dot }"
              @click="scrollTo(dot)"
              aria-label="Go to slide"
            />
          </div>

          <div class="hidden md:grid md:grid-cols-3 md:gap-8">
            <div
              v-for="(feature, index) in features"
              :key="feature.title"
              v-motion
              class="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-6 border border-slate-700 hover:border-blue-500/50 transition-all"
              :initial="{ opacity: 0, y: 20 }"
              :visible-once="{ opacity: 1, y: 0 }"
              :duration="600"
              :delay="400 + index * 100"
              :hovered="{ scale: 1.05, y: -5 }"
            >
              <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-blue-500 to-blue-600 flex items-center justify-center mb-4">
                <component :is="feature.icon" class="w-6 h-6 text-white" />
              </div>
              <h4 class="text-xl font-bold text-white mb-3">{{ feature.title }}</h4>
              <p class="text-slate-400 leading-relaxed">{{ feature.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
