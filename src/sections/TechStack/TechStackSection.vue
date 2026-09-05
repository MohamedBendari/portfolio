<script setup>
import {
  Layers,
  Code2,
  Component,
  Braces,
  Server,
  Route,
  Database,
  Leaf,
  Wind,
  GitBranch,
  Github,
  Globe,
  Container,
  Terminal,
  ScanText,
  Sparkles,
} from 'lucide-vue-next'

// Category -> visual accent (gradient pair used for icon bg, glow, border)
const categoryAccents = {
  Frontend: { from: '#34d399', to: '#0ea5e9', glow: 'rgba(52, 211, 153, 0.35)' },
  Backend: { from: '#818cf8', to: '#6366f1', glow: 'rgba(99, 102, 241, 0.35)' },
  Database: { from: '#fbbf24', to: '#f97316', glow: 'rgba(251, 191, 36, 0.35)' },
  DevOps: { from: '#c084fc', to: '#d946ef', glow: 'rgba(192, 132, 252, 0.35)' },
  AI: { from: '#fb7185', to: '#ec4899', glow: 'rgba(251, 113, 133, 0.35)' },
}

// Single source of truth for the grid
const techStack = [
  { name: 'Laravel', category: 'Backend', icon: Layers },
  { name: 'PHP', category: 'Backend', icon: Code2 },
  { name: 'Vue.js', category: 'Frontend', icon: Component },
  { name: 'JavaScript', category: 'Frontend', icon: Braces },
  { name: 'Node.js', category: 'Backend', icon: Server },
  { name: 'Express.js', category: 'Backend', icon: Route },
  { name: 'MySQL', category: 'Database', icon: Database },
  { name: 'MongoDB', category: 'Database', icon: Leaf },
  { name: 'Tailwind CSS', category: 'Frontend', icon: Wind },
  { name: 'Git', category: 'DevOps', icon: GitBranch },
  { name: 'GitHub', category: 'DevOps', icon: Github },
  { name: 'REST API', category: 'Backend', icon: Globe },
  { name: 'Docker', category: 'DevOps', icon: Container },
  { name: 'Python', category: 'Backend', icon: Terminal },
  { name: 'OCR', category: 'AI', icon: ScanText },
  { name: 'OpenAI API', category: 'AI', icon: Sparkles },
].map((tech) => ({ ...tech, accent: categoryAccents[tech.category] }))
</script>

<template>
  <section
    id="tech-stack"
    aria-labelledby="tech-stack-heading"
    class="relative bg-neutral-950 py-24 sm:py-28 lg:py-32"
  >
    <!-- Ambient background glow -->
    <div
      class="pointer-events-none absolute inset-0 overflow-hidden"
      aria-hidden="true"
    >
      <div
        class="absolute left-1/2 top-0 h-[420px] w-[420px] -translate-x-1/2 rounded-full bg-indigo-500/10 blur-[120px]"
      ></div>
    </div>

    <div class="relative mx-auto max-w-7xl px-6 lg:px-8">
      <!-- Section header -->
      <div class="mx-auto max-w-2xl text-center">
        <span
          class="inline-block text-xs font-semibold uppercase tracking-[0.2em] text-indigo-400"
        >
          Tech Stack
        </span>
        <h2
          id="tech-stack-heading"
          class="mt-3 text-3xl font-bold tracking-tight text-white sm:text-4xl"
        >
          Technologies I Work With
        </h2>
        <p class="mt-4 text-base leading-relaxed text-neutral-400 sm:text-lg">
          I build scalable, secure and modern web applications using
          industry-standard technologies across frontend, backend and AI
          automation.
        </p>
      </div>

      <!-- Tech grid -->
      <ul
        class="mt-16 grid grid-cols-2 gap-4 sm:gap-5 md:grid-cols-3 lg:grid-cols-4"
        role="list"
      >
        <li
          v-for="(tech, index) in techStack"
          :key="tech.name"
          tabindex="0"
          role="listitem"
          :aria-label="`${tech.name}, ${tech.category}`"
          class="tech-card group relative flex flex-col items-center gap-3 rounded-2xl border border-white/10 bg-white/[0.03] p-6 text-center backdrop-blur-md transition-all duration-300 ease-out hover:-translate-y-1 hover:border-white/20 focus-visible:-translate-y-1 focus-visible:border-white/20 focus-visible:outline-none"
          :style="{ '--accent-glow': tech.accent.glow }"
        >
          <!-- Icon -->
          <span
            class="flex h-12 w-12 items-center justify-center rounded-xl transition-transform duration-300 ease-out group-hover:scale-110"
            :style="{
              background: `linear-gradient(135deg, ${tech.accent.from}22, ${tech.accent.to}22)`,
            }"
            aria-hidden="true"
          >
            <component
              :is="tech.icon"
              class="h-6 w-6"
              :style="{ color: tech.accent.from }"
              stroke-width="1.75"
            />
          </span>

          <!-- Name -->
          <span class="text-sm font-semibold text-white sm:text-base">
            {{ tech.name }}
          </span>

          <!-- Category -->
          <span class="text-xs font-medium text-neutral-500">
            {{ tech.category }}
          </span>

          <!-- fade-up stagger -->
          <span
            class="sr-only"
            aria-hidden="true"
            :style="{ animationDelay: `${index * 60}ms` }"
          ></span>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.tech-card {
  opacity: 0;
  animation: fadeUp 0.6s ease-out forwards;
}

/* Stagger each card individually using nth-child, matching v-for order */
.tech-card:nth-child(1) { animation-delay: 0ms; }
.tech-card:nth-child(2) { animation-delay: 60ms; }
.tech-card:nth-child(3) { animation-delay: 120ms; }
.tech-card:nth-child(4) { animation-delay: 180ms; }
.tech-card:nth-child(5) { animation-delay: 240ms; }
.tech-card:nth-child(6) { animation-delay: 300ms; }
.tech-card:nth-child(7) { animation-delay: 360ms; }
.tech-card:nth-child(8) { animation-delay: 420ms; }
.tech-card:nth-child(9) { animation-delay: 480ms; }
.tech-card:nth-child(10) { animation-delay: 540ms; }
.tech-card:nth-child(11) { animation-delay: 600ms; }
.tech-card:nth-child(12) { animation-delay: 660ms; }
.tech-card:nth-child(13) { animation-delay: 720ms; }
.tech-card:nth-child(14) { animation-delay: 780ms; }
.tech-card:nth-child(15) { animation-delay: 840ms; }
.tech-card:nth-child(16) { animation-delay: 900ms; }

@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Glow + border animation on hover/focus, using the per-card accent color */
.tech-card:hover,
.tech-card:focus-visible {
  box-shadow: 0 0 40px -8px var(--accent-glow);
}

@media (prefers-reduced-motion: reduce) {
  .tech-card {
    animation: none;
    opacity: 1;
  }
}
</style>