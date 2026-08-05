<!-- layouts/default.vue -->
<template>
  <div class="layout-container">
    <!-- Render your isolated component -->
    <Header />

    <main class="main-content">
      <slot />
    </main>

    <footer class="site-footer">
      <p>&copy; 2026 My App. All rights reserved.</p>
    </footer>
  </div>
</template>

<style scoped>
.layout-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  font-family: system-ui, sans-serif;
}
.main-content {
  flex-grow: 1;
}
.site-footer {
  background-color: white;
  color: #4b5563;
  text-align: center;
  padding: 1rem;
  border-top: 1px solid #e5e7eb;
}
</style>
