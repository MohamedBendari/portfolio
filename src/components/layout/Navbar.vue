<script setup>
import { ref } from "vue"
import { Menu } from "lucide-vue-next"

import Logo from "./Logo.vue"
import NavLinks from "./NavLinks.vue"
import MobileMenu from "./MobileMenu.vue"
import HireMeButton from "./HireMeButton.vue"

import { navLinks } from "@/data/navLinks"
import { useScrollSpy } from "@/composables/useScrollSpy"

const mobileOpen = ref(false)

const { activeSection, isScrolled, scrollToSection } = useScrollSpy([
  "home",
  "about",
  "Services",
  "projects",
  "experience",
  "contact",
])

const toggleMenu = () => {
  mobileOpen.value = !mobileOpen.value
}
</script>

<template>
  <header
    class="fixed left-0 top-0 z-50 w-full transition-all duration-300"
    :class="
      isScrolled
        ? 'bg-slate-900/80 backdrop-blur-xl shadow-lg border-b border-white/10'
        : 'bg-transparent'
    "
  >
    <div class="mx-auto flex max-w-7xl items-center justify-between px-6 py-4">

      <Logo />

      <NavLinks
        :links="navLinks"
        :active-section="activeSection"
        :scroll-to-section="scrollToSection"
      />

      <div class="flex items-center gap-4">

        <HireMeButton />

        <button
          class="text-white lg:hidden"
          @click="toggleMenu"
          aria-label="Open Menu"
        >
          <Menu :size="28" />
        </button>

      </div>

    </div>

    <MobileMenu
      :is-open="mobileOpen"
      :links="navLinks"
      :active-section="activeSection"
      :scroll-to-section="scrollToSection"
      @close="mobileOpen = false"
    />

  </header>
</template>