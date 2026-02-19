<script setup>
import { computed, onMounted, onUnmounted, ref } from 'vue'
import HeroSection from '@/components/landing/HeroSection.vue'
import WhyUsSection from '@/components/landing/WhyUsSection.vue'
import ExpertiseSection from '@/components/landing/ExpertiseSection.vue'
import ProcessSection from '@/components/landing/ProcessSection.vue'
import CaseStudiesSection from '@/components/landing/CaseStudiesSection.vue'
import CTASection from '@/components/landing/CTASection.vue'
import Footer from '@/components/landing/Footer.vue'

const scrollProgress = ref(0)
let targetProgress = 0
let rafId = null

const updateTarget = () => {
  const { scrollTop, scrollHeight, clientHeight } = document.documentElement
  const max = scrollHeight - clientHeight
  targetProgress = max > 0 ? scrollTop / max : 0

  if (rafId === null) {
    rafId = requestAnimationFrame(tick)
  }
}

const tick = () => {
  scrollProgress.value += (targetProgress - scrollProgress.value) * 0.15

  if (Math.abs(targetProgress - scrollProgress.value) < 0.001) {
    scrollProgress.value = targetProgress
    rafId = null
    return
  }

  rafId = requestAnimationFrame(tick)
}

onMounted(() => {
  updateTarget()
  window.addEventListener('scroll', updateTarget, { passive: true })
  window.addEventListener('resize', updateTarget)
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateTarget)
  window.removeEventListener('resize', updateTarget)
  if (rafId !== null) {
    cancelAnimationFrame(rafId)
    rafId = null
  }
})

const progressStyle = computed(() => ({
  transform: `scaleX(${scrollProgress.value})`,
}))
</script>

<template>
  <div class="bg-slate-50">
    <div
      class="fixed top-0 left-0 right-0 h-1 bg-gradient-to-r from-blue-500 via-blue-600 to-orange-500 origin-left z-50"
      :style="progressStyle"
    />

    <HeroSection />
    <WhyUsSection />
    <ExpertiseSection />
    <ProcessSection />
    <CaseStudiesSection />
    <CTASection />
    <Footer />
  </div>
</template>
