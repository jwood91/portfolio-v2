<script setup lang="ts">
import VueTypewriterEffect from "vue-typewriter-effect";
// In Nuxt 4, defineComponent, ref, and computed are automatically imported.
// The array must live inside the script context so the template can see it.
const items = [
  'https://picsum.photos/468/468?random=1',
  'https://picsum.photos/468/468?random=2',
  'https://picsum.photos/468/468?random=3',
  'https://picsum.photos/468/468?random=4',
  'https://picsum.photos/468/468?random=5',
  'https://picsum.photos/468/468?random=6'
]

const isReady = ref(false)

onMounted(() => {
  // 2. Flip the switch only after the component is completely mounted
  isReady.value = true
})
</script>

<template>
  <div>
    <div class="hero-container">
      <div class="hero-content-container">
        <vue-typewriter-effect v-show="isReady" :strings="['Hello, my name is Joe, I am a web developer']" />
        <h1 class="font-bold text-blue-600"> </h1>
        <div class="circle-image"></div>    
      </div>    
    </div>

    <div class="p-8 max-w-4xl mx-auto">
      <UCarousel
        v-slot="{ item }"
        loop
        wheel-gestures
        :auto-scroll="{ speed: 0.5, stopOnInteraction: false }"
        :items="items"
        :ui="{ item: 'basis-1/3 p-2' }"
      >
        <img :src="item" width="234" height="234" class="rounded-lg object-cover" loading="lazy">
      </UCarousel>
    </div>
  </div>
</template>

<style scoped>
/* Removed lang="ts" as styles are standard CSS */
.hero-container {
  margin: 0 auto;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: grey;
}
.hero-content-container {
  max-width: 1200px;
  width: 100%;
  height: 100vh;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

:deep(.Typewriter__wrapper) {
    font-size: 40px;
}

:deep(#typewriter) {
      max-width: 400px;
}

:deep(.Typewriter__cursor) {
    font-size: 40px;
}
</style>
