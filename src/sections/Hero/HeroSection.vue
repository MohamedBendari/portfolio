<template>
  <section
    id="home"
    aria-label="Introduction"
    class="relative flex min-h-screen items-center overflow-hidden bg-slate-950 pb-20 pt-36"
  >
    <!-- Background layer: grid + blur circles -->
    <div class="pointer-events-none absolute inset-0" aria-hidden="true">
      <div
        class="absolute inset-0 opacity-[0.05]
               bg-[linear-gradient(to_right,rgba(255,255,255,0.6)_1px,transparent_1px),linear-gradient(to_bottom,rgba(255,255,255,0.6)_1px,transparent_1px)]
               bg-[size:56px_56px]"
      />
      <div class="absolute -left-40 -top-40 h-96 w-96 rounded-full bg-purple-600/30 blur-3xl" />
      <div class="absolute -right-32 top-1/3 h-[28rem] w-[28rem] rounded-full bg-blue-600/20 blur-3xl" />
      <div class="absolute bottom-0 left-1/4 h-72 w-72 rounded-full bg-purple-500/10 blur-3xl" />
    </div>

    <div class="relative mx-auto grid w-full max-w-6xl grid-cols-1 items-center gap-16 px-6 lg:grid-cols-2 lg:gap-12">
      <!-- Left column: content -->
      <div class="flex flex-col items-start text-left">
        <p
          class="hero-fade-in mb-6 inline-flex items-center gap-2 rounded-full border border-white/10
                 bg-white/5 px-4 py-1.5 text-sm text-white/80 backdrop-blur-sm"
        >
          <span class="relative flex h-2 w-2" aria-hidden="true">
            <span class="absolute inline-flex h-full w-full animate-ping rounded-full bg-green-400 opacity-75" />
            <span class="relative inline-flex h-2 w-2 rounded-full bg-green-400" />
          </span>
          Available for Freelance
        </p>

        <p class="hero-fade-in hero-delay-1 text-lg text-white/70 sm:text-xl">Hi, I'm</p>

        <h1 class="hero-fade-in hero-delay-2 mt-1 text-5xl font-extrabold tracking-tight text-white sm:text-6xl lg:text-7xl">
          Ahsan
          <span class="bg-gradient-to-r from-purple-400 via-blue-400 to-purple-400 bg-clip-text text-transparent">
            Ali
          </span>
        </h1>

        <p
          class="hero-fade-in hero-delay-3 mt-4 flex h-8 items-center text-xl font-semibold text-purple-300 sm:text-2xl"
          :aria-label="rolesForScreenReader"
        >
          <span aria-hidden="true">{{ displayText }}</span>
          <span class="typing-cursor" aria-hidden="true">|</span>
        </p>

        <p class="hero-fade-in hero-delay-4 mt-6 max-w-xl text-base leading-relaxed text-white/60 sm:text-lg">
          I build modern web applications with
          <strong class="font-semibold text-white/80">Laravel</strong>,
          <strong class="font-semibold text-white/80">Vue.js</strong>, and
          <strong class="font-semibold text-white/80">Node.js</strong> —
          crafting fast, scalable REST APIs and automating workflows that save teams real time.
        </p>

        <ul class="hero-fade-in hero-delay-5 mt-8 flex flex-wrap gap-2" aria-label="Technology stack">
          <li v-for="tech in techStack" :key="tech.label">
            <TechBadge :label="tech.label" :dot-color="tech.dotColor" />
          </li>
        </ul>

        <div class="hero-fade-in hero-delay-6 mt-10 flex flex-wrap items-center gap-4">
          <BaseButton tag="a" href="#projects" variant="primary">
            View Projects
            <template #icon-right>
              <ArrowRight :size="18" class="transition-transform duration-300 group-hover:translate-x-1" />
            </template>
          </BaseButton>

          <BaseButton tag="a" href="/resume-ahsan-ali.pdf" download variant="secondary">
            <template #icon-left>
              <Download :size="18" />
            </template>
            Download CV
          </BaseButton>
        </div>
      </div>

      <!-- Right column: illustration -->
      <div
        class="hero-fade-in hero-delay-3 relative mx-auto flex h-[380px] w-full max-w-md items-center justify-center sm:h-[440px] lg:h-[480px]"
        aria-hidden="true"
      >
        <!-- gradient glow circle -->
        <div class="float-slow absolute h-72 w-72 rounded-full bg-gradient-to-br from-purple-600/40 via-blue-600/30 to-transparent blur-2xl" />

        <!-- laptop placeholder -->
        <div class="relative flex h-56 w-72 flex-col rounded-xl border border-white/10 bg-slate-900/60 shadow-2xl shadow-purple-950/40 backdrop-blur-md sm:h-64 sm:w-80">
          <div class="flex items-center gap-1.5 border-b border-white/10 px-3 py-2">
            <span class="h-2 w-2 rounded-full bg-white/20" />
            <span class="h-2 w-2 rounded-full bg-white/20" />
            <span class="h-2 w-2 rounded-full bg-white/20" />
          </div>
          <div class="flex flex-1 items-center justify-center">
            <Code2 :size="48" class="text-purple-400/60" />
          </div>
        </div>

        <!-- floating code window -->
        <CodeWindowMockup class="float-medium absolute -bottom-10 -left-8 hidden sm:block" />

        <!-- floating tech badges -->
        <span class="float-fast absolute -top-4 right-2 rounded-lg border border-white/10 bg-white/5 px-3 py-1.5 text-xs font-medium text-white/80 shadow-lg backdrop-blur-sm">
          ⚡ Vue 3
        </span>
        <span class="float-medium absolute -right-8 top-1/4 hidden rounded-lg border border-white/10 bg-white/5 px-3 py-1.5 text-xs font-medium text-white/80 shadow-lg backdrop-blur-sm sm:block">
          🚀 Laravel
        </span>
        <span class="float-slow absolute bottom-2 right-0 rounded-lg border border-white/10 bg-white/5 px-3 py-1.5 text-xs font-medium text-white/80 shadow-lg backdrop-blur-sm">
          🟢 Node.js
        </span>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed } from 'vue'
import { ArrowRight, Download, Code2 } from 'lucide-vue-next'
import BaseButton from '@/components/ui/BaseButton.vue'
import TechBadge from '@/components/ui/TechBadge.vue'
import CodeWindowMockup from '@/components/ui/CodeWindowMockup.vue'
import { roles, techStack } from '@/data/heroData'
import { useTypingEffect } from '@/composables/useTypingEffect'

const { displayText } = useTypingEffect(roles)

// Static accessible label so screen readers get the full list once,
// instead of the rapidly changing animated text.
const rolesForScreenReader = computed(() => roles.join(', '))
</script>

<style scoped>
@keyframes fadeSlideUp {
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero-fade-in {
  animation: fadeSlideUp 0.7s ease-out both;
}

.hero-delay-1 { animation-delay: 0.08s; }
.hero-delay-2 { animation-delay: 0.16s; }
.hero-delay-3 { animation-delay: 0.24s; }
.hero-delay-4 { animation-delay: 0.32s; }
.hero-delay-5 { animation-delay: 0.4s; }
.hero-delay-6 { animation-delay: 0.48s; }

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-14px); }
}

.float-slow { animation: float 6s ease-in-out infinite; }
.float-medium { animation: float 4.5s ease-in-out infinite; }
.float-fast { animation: float 3s ease-in-out infinite; }

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.typing-cursor {
  display: inline-block;
  margin-left: 2px;
  animation: blink 1s step-end infinite;
}

@media (prefers-reduced-motion: reduce) {
  .hero-fade-in,
  .float-slow,
  .float-medium,
  .float-fast,
  .typing-cursor {
    animation: none !important;
  }
}
</style>