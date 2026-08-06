<script setup lang="ts">
import VueTypewriterEffect from "vue-typewriter-effect";
// In Nuxt 4, defineComponent, ref, and computed are automatically imported.
// The array must live inside the script context so the template can see it.
const techStack = [
  { name: 'Vue.js', icon: 'i-simple-icons-vuedotjs', color: 'group-hover:text-[#4FC08D]' },
  { name: 'SQL', icon: 'i-simple-icons-mysql', color: 'group-hover:text-[#4479A1]' }, // Using standard MySQL logo for SQL
  { name: 'Laravel', icon: 'i-simple-icons-laravel', color: 'group-hover:text-[#FF2D20]' },
  { name: 'TypeScript', icon: 'i-simple-icons-typescript', color: 'group-hover:text-[#3178C6]' },
  { name: 'PHP', icon: 'i-simple-icons-php', color: 'group-hover:text-[#777BB4]' },
  { name: 'JavaScript', icon: 'i-simple-icons-javascript', color: 'group-hover:text-[#F7DF1E]' },
  { name: 'Docker', icon: 'i-simple-icons-docker', color: 'group-hover:text-[#2496ED]' },
  { name: 'WordPress', icon: 'i-simple-icons-wordpress', color: 'group-hover:text-[#21759B]' },
  { name: 'Bedrock', icon: 'i-simple-icons-roots', color: 'group-hover:text-[#525DDC]' }, // Roots Bedrock uses the Roots logo
  { name: 'jQuery', icon: 'i-simple-icons-jquery', color: 'group-hover:text-[#0769AD]' },
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
        
        <div class="text-content">
          <vue-typewriter-effect v-show="isReady" :strings="['Hello, my name is Joe,\nI am a web developer']" />
        </div> 

        <div class="circle-image"></div>   

      </div>
          
    </div>

   <div class="w-full max-w-4xl mx-auto py-8">
    <UCarousel
      v-slot="{ item }"
      :items="techStack"
      loop
      :auto-scroll="{ speed: 0.7, stopOnInteraction: true}"
      :ui="{
        container: 'ms-0',
        item: 'basis-1/3 sm:basis-1/5 md:basis-1/8 px-3 justify-center'
      }"
    >
      <!-- w-full lets the card scale safely inside the layout boundaries -->
      <div 
        class="group flex flex-col items-center justify-center p-4 w-full h-24 rounded-xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900 cursor-pointer shadow-sm hover:shadow-md hover:border-primary-500 transition-all duration-300 ease-out"
      >
        <UIcon 
          :name="item.icon" 
          :class="[
            'w-10 h-10 transition-all duration-300 ease-out group-hover:scale-125 group-hover:-translate-y-1 group-hover:rotate-6',
            item.color,
            'text-gray-400'
          ]"
        />
        <span class="text-xs font-medium mt-2 text-gray-500 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-gray-100 transition-colors duration-200">
          {{ item.name }}
        </span>
      </div>
    </UCarousel>
  </div>

  </div>
</template>

<style scoped>
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
  padding: 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center; 
  gap: 2rem; 
}

:deep(.Typewriter__wrapper) {
  font-size: 40px;
  white-space: pre-line;
}

:deep(.Typewriter__cursor) {
  font-size: 40px;
}

.text-content {
  flex: 1; 
  height: 120px;          
  display: flex;
  flex-direction: column;
  justify-content: center; 
}

.circle-image {
  width: 300px;         
  height: 300px;        
  border-radius: 50%;   
  background-image: url('https://picsum.photos/468/468?random=1'); 
  background-size: cover;
  background-position: center;
  flex-shrink: 0;       
  border: 4px solid white; 
}

@media (max-width: 768px) {
  .hero-content-container {
    flex-direction: column-reverse; 
    justify-content: flex-start;            
    padding-top: 15vh;
    gap: 2rem;                   
    height: 100dvh;        
    min-height: 100dvh;    
  }

  .text-content {
    text-align: center;            
    flex: none;                    
    width: 100%;
    height: 120px; 
    display: flex;
    flex-direction: column;
    justify-content: flex-start; 
  }

  :deep(.Typewriter__wrapper),
  :deep(.Typewriter__cursor) {
    font-size: 28px;               
  }

  .circle-image {
    width: 200px;                  
    height: 200px;
    flex-shrink: 0; 
  }
}
</style>

