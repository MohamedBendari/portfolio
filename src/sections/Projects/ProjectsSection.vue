<script setup>
import {
  Github,
  ExternalLink,
  Check,
  Boxes,
  FileScan,
  MessagesSquare,
  LayoutGrid,
} from 'lucide-vue-next'

// Single source of truth for all project cards
const projects = [
  {
    title: 'Asset Management System',
    description:
      'A professional admin dashboard for tracking, assigning and auditing company assets at scale.',
    icon: Boxes,
    gradient: { from: '#6366f1', to: '#0ea5e9' },
    features: [
      'Role Based Authentication',
      'QR Code Asset Tracking',
      'Inventory Management',
      'Professional Admin Dashboard',
    ],
    techs: ['Laravel', 'Vue.js', 'MySQL'],
    githubUrl: 'https://github.com/ahsanali35103/asset-management-system.git'
  },
  {
    title: 'AI Powered PDF Processor',
    description:
      'An intelligent document pipeline that extracts, reads and structures data from scanned PDFs automatically.',
    icon: FileScan,
    gradient: { from: '#f97316', to: '#ec4899' },
    features: [
      'OCR Text Extraction',
      'AI Processing Pipeline',
      'OpenAI-Powered Document Understanding',
    ],
    techs: ['Laravel', 'Python', 'OCR', 'OpenAI API', 'MongoDB'],
    githubUrl: 'https://github.com/ahsanali35103/ai-powered-pdf-processor.git'
  },
  {
    title: 'Real-Time Chat Application',
    description:
      'A team-based messaging platform with live channels, instant delivery and secure authentication.',
    icon: MessagesSquare,
    gradient: { from: '#22c55e', to: '#0ea5e9' },
    features: [
      'Channels & Teams',
      'Real-Time Messaging',
      'Authentication',
    ],
    techs: ['Laravel', 'Vue.js', 'Node.js'],
    githubUrl: 'https://github.com/ahsanali35103/chat-app-laravel.git'
  },
  {
    title: 'Developer Portfolio',
    description:
      'A modern, responsive personal portfolio built to showcase projects and technical expertise.',
    icon: LayoutGrid,
    gradient: { from: '#a855f7', to: '#6366f1' },
    features: ['Modern UI', 'Fully Responsive Design'],
    techs: ['Vue.js', 'Tailwind CSS'],
    githubUrl: '#'
  },
]
</script>

<template>
  <section
    id="projects"
    aria-labelledby="projects-heading"
    class="relative bg-neutral-950 py-24 sm:py-28 lg:py-32"
  >
    <div class="relative mx-auto max-w-7xl px-6 lg:px-8">
      <!-- Section header -->
      <div class="mx-auto max-w-2xl text-center">
        <span
          class="inline-block text-xs font-semibold uppercase tracking-[0.2em] text-indigo-400"
        >
          Featured Projects
        </span>
        <h2
          id="projects-heading"
          class="mt-3 text-3xl font-bold tracking-tight text-white sm:text-4xl"
        >
          Projects That Showcase My Skills
        </h2>
        <p class="mt-4 text-base leading-relaxed text-neutral-400 sm:text-lg">
          A collection of real-world applications demonstrating my
          experience in Laravel, Vue.js, Node.js and AI Automation.
        </p>
      </div>

      <!-- Projects grid -->
      <ul
        role="list"
        class="mt-16 grid grid-cols-1 gap-6 md:grid-cols-2 md:gap-8"
      >
        <li
          v-for="(project, index) in projects"
          :key="project.title"
          class="project-card group relative rounded-3xl border border-white/10 bg-white/[0.03] backdrop-blur-md transition-all duration-300 ease-out hover:-translate-y-1.5 hover:border-white/20"
          :style="{
            animationDelay: `${index * 80}ms`,
            '--glow-from': project.gradient.from,
            '--glow-to': project.gradient.to,
          }"
        >
          <article class="flex h-full flex-col overflow-hidden rounded-3xl">
            <!-- Image placeholder -->
            <div
              class="relative flex h-52 items-center justify-center overflow-hidden sm:h-60"
              :style="{
                background: `linear-gradient(135deg, ${project.gradient.from}33, ${project.gradient.to}33)`,
              }"
              aria-hidden="true"
            >
              <!-- Dot-grid texture -->
              <div class="dot-grid absolute inset-0 opacity-30"></div>
              <!-- Center icon -->
              <div
                class="relative flex h-16 w-16 items-center justify-center rounded-2xl border border-white/10 bg-white/10 backdrop-blur-sm transition-transform duration-300 ease-out group-hover:scale-110 sm:h-20 sm:w-20"
              >
                <component
                  :is="project.icon"
                  class="h-8 w-8 text-white sm:h-9 sm:w-9"
                  stroke-width="1.5"
                />
              </div>
            </div>

            <!-- Content -->
            <div class="flex flex-1 flex-col p-6 sm:p-7">
              <h3 class="text-lg font-bold text-white sm:text-xl">
                {{ project.title }}
              </h3>
              <p class="mt-2 text-sm leading-relaxed text-neutral-400 sm:text-base">
                {{ project.description }}
              </p>

              <!-- Feature list -->
              <ul role="list" class="mt-4 space-y-2">
                <li
                  v-for="feature in project.features"
                  :key="feature"
                  class="flex items-start gap-2 text-sm text-neutral-300"
                >
                  <Check
                    class="mt-0.5 h-4 w-4 shrink-0 text-emerald-400"
                    stroke-width="2"
                    aria-hidden="true"
                  />
                  {{ feature }}
                </li>
              </ul>

              <!-- Tech badges -->
              <ul
                role="list"
                aria-label="Technologies used"
                class="mt-5 flex flex-wrap gap-2"
              >
                <li
                  v-for="tech in project.techs"
                  :key="tech"
                  class="rounded-full border border-white/10 bg-white/[0.04] px-3 py-1 text-xs font-medium text-neutral-300"
                >
                  {{ tech }}
                </li>
              </ul>

              <!-- Actions -->
             <div class="mt-6 flex flex-wrap items-center gap-3 pt-2">
  <a
    :href="project.githubUrl"
    target="_blank"
    rel="noopener noreferrer"
    :aria-label="`View ${project.title} source code on GitHub`"
    class="inline-flex items-center gap-2 rounded-xl border border-white/15 bg-white/[0.04] px-4 py-2.5 text-sm font-medium text-white transition-all duration-300 ease-out hover:border-white/30 hover:bg-white/[0.08] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-400"
  >
    <Github class="h-4 w-4" aria-hidden="true" />
    GitHub
  </a>

</div>
            </div>
          </article>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.project-card {
  opacity: 0;
  animation: fadeUp 0.6s ease-out forwards;
}

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

/* Glow + gradient border effect on hover/focus-within */
.project-card:hover,
.project-card:focus-within {
  box-shadow: 0 0 50px -12px color-mix(in srgb, var(--glow-from) 45%, transparent);
}

.project-card::before {
  content: '';
  position: absolute;
  inset: -1px;
  z-index: -1;
  border-radius: 1.5rem;
  padding: 1px;
  background: linear-gradient(135deg, var(--glow-from), var(--glow-to));
  opacity: 0;
  transition: opacity 0.3s ease-out;
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
}

.project-card:hover::before,
.project-card:focus-within::before {
  opacity: 0.6;
}

.dot-grid {
  background-image: radial-gradient(rgba(255, 255, 255, 0.35) 1px, transparent 1px);
  background-size: 18px 18px;
}

@media (prefers-reduced-motion: reduce) {
  .project-card {
    animation: none;
    opacity: 1;
  }
}
</style>