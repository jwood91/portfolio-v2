<!-- components/AppHeader.vue -->
<template>
  <header class="site-header">
    <div class="header-container">
      <NuxtLink to="/" class="logo" @click="closeMenu">My App</NuxtLink>

      <!-- Hamburger Button (Visible only on mobile via CSS) -->
      <button 
        class="hamburger" 
        :class="{ 'is-active': isOpen }" 
        @click="toggleMenu"
        aria-label="Toggle menu"
        :aria-expanded="isOpen"
      >
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>

      <!-- Navigation Menu -->
      <nav class="nav-menu" :class="{ 'is-open': isOpen }">
        <NuxtLink to="/about" @click="closeMenu">About</NuxtLink>
        <NuxtLink to="/services" @click="closeMenu">Services</NuxtLink>
        <NuxtLink to="/contact" @click="closeMenu">Contact</NuxtLink>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const isOpen = ref(false)

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const closeMenu = () => {
  isOpen.value = false
}
</script>

<style scoped>
.site-header {
  background: #ffffff;
  border-bottom: 1px solid #e5e7eb;
  position: sticky;
  top: 0;
  z-index: 100;
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-weight: bold;
  text-decoration: none;
  color: #111827;
}

/* Hamburger Icon Styling */
.hamburger {
  display: none; /* Hidden on desktop */
  flex-direction: column;
  gap: 6px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}

.bar {
  display: block;
  width: 24px;
  height: 2px;
  background-color: #111827;
  transition: transform 0.3s, opacity 0.3s;
}

/* Hamburger Transform to 'X' when open */
.hamburger.is-active .bar:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}
.hamburger.is-active .bar:nth-child(2) {
  opacity: 0;
}
.hamburger.is-active .bar:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
}

/* Desktop Navigation */
.nav-menu {
  display: flex;
  gap: 1.5rem;
}

.nav-menu a {
  text-decoration: none;
  color: #4b5563;
}

.nav-menu .router-link-active {
  color: #2563eb;
  font-weight: 600;
}

/* Mobile Responsive Styles */
@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .nav-menu {
    display: none; /* Hide default menu */
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background: #ffffff;
    border-bottom: 1px solid #e5e7eb;
    flex-direction: column;
    padding: 1rem;
    gap: 1rem;
    box-sizing: border-box;
  }

  .nav-menu.is-open {
    display: flex; /* Show dropdown when open */
  }
}
</style>