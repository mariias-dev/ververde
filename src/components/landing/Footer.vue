<script setup>
import { Linkedin, Twitter, Instagram, Mail } from 'lucide-vue-next'

const navigation = [
  { name: 'Home', href: '#home' },
  { name: 'Services', href: '#services' },
  { name: 'Case Studies', href: '#case-studies' },
  { name: 'Contact', href: '#cta' },
]

const socials = [
  { name: 'LinkedIn', icon: Linkedin, href: '#' },
  { name: 'X (Twitter)', icon: Twitter, href: '#' },
  { name: 'Instagram', icon: Instagram, href: '#' },
]

const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="bg-slate-900 text-slate-300 relative overflow-hidden">
    <div class="h-1 bg-gradient-to-r from-blue-500 via-purple-500 to-orange-500" />

    <div class="max-w-7xl mx-auto px-6 py-16">
      <div class="grid md:grid-cols-2 gap-12 mb-12">
        <div
          v-motion
          :initial="{ opacity: 0, y: 20 }"
          :visible-once="{ opacity: 1, y: 0 }"
          :duration="600"
        >
          <h3 class="text-3xl font-bold bg-gradient-to-r from-blue-400 to-orange-400 bg-clip-text text-transparent mb-4">
            VERVERDE
          </h3>
          <p class="text-slate-400 leading-relaxed mb-6 max-w-md">
            A UK-based performance marketing agency that turns your ad spend into tangible revenue.
            Data-driven. Results-focused. No fluff.
          </p>

          <a
            href="mailto:ververde_ltd@yahoo.com"
            class="inline-flex items-center gap-2 text-blue-400 hover:text-blue-300 transition-colors"
          >
            <Mail class="w-4 h-4" />
            ververde_ltd@yahoo.com
          </a>
        </div>

        <div
          v-motion
          class="grid sm:grid-cols-2 gap-8"
          :initial="{ opacity: 0, y: 20 }"
          :visible-once="{ opacity: 1, y: 0 }"
          :duration="600"
          :delay="200"
        >
          <div>
            <h4 class="text-white font-semibold mb-4">Navigation</h4>
            <ul class="space-y-3">
              <li v-for="item in navigation" :key="item.name">
                <a :href="item.href" class="text-slate-400 hover:text-white transition-colors">
                  {{ item.name }}
                </a>
              </li>
            </ul>
          </div>

          <div>
            <h4 class="text-white font-semibold mb-4">Follow Us</h4>
            <div class="flex gap-3">
              <a
                v-for="social in socials"
                :key="social.name"
                :href="social.href"
                class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-gradient-to-br hover:from-blue-500 hover:to-orange-500 transition-all hover:scale-110"
                :aria-label="social.name"
              >
                <component :is="social.icon" class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>
      </div>

      <div class="border-t border-slate-800 pt-8">
        <div
          v-motion
          class="flex flex-col md:flex-row justify-between items-center gap-4 text-sm text-slate-500"
          :initial="{ opacity: 0 }"
          :visible-once="{ opacity: 1 }"
          :duration="600"
          :delay="400"
        >
          <div class="text-center md:text-left">
            <p class="font-medium text-slate-400 mb-1">VERVERDE LTD</p>
            <p class="text-xs">
              Registered Office: 71-75, Shelton Street, Covent Garden, London, WC2H 9JQ, UNITED KINGDOM
            </p>
          </div>

          <p class="text-slate-500">
            © {{ currentYear }} VERVERDE LTD. All rights reserved.
          </p>
        </div>
      </div>
    </div>

    <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-slate-700 to-transparent" />
  </footer>
</template>
