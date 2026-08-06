<script setup lang="ts">
import VueTypewriterEffect from "vue-typewriter-effect";

const techStack = [
  { name: 'Vue.js', icon: 'i-simple-icons-vuedotjs', color: 'group-hover:text-[#4FC08D]' },
  { name: 'SQL', icon: 'i-simple-icons-mysql', color: 'group-hover:text-[#4479A1]' },
  { name: 'Laravel', icon: 'i-simple-icons-laravel', color: 'group-hover:text-[#FF2D20]' },
  { name: 'TypeScript', icon: 'i-simple-icons-typescript', color: 'group-hover:text-[#3178C6]' },
  { name: 'PHP', icon: 'i-simple-icons-php', color: 'group-hover:text-[#777BB4]' },
  { name: 'JavaScript', icon: 'i-simple-icons-javascript', color: 'group-hover:text-[#F7DF1E]' },
  { name: 'Docker', icon: 'i-simple-icons-docker', color: 'group-hover:text-[#2496ED]' },
  { name: 'WordPress', icon: 'i-simple-icons-wordpress', color: 'group-hover:text-[#21759B]' },
  { name: 'Bedrock', icon: 'i-simple-icons-roots', color: 'group-hover:text-[#525DDC]' },
  { name: 'jQuery', icon: 'i-simple-icons-jquery', color: 'group-hover:text-[#0769AD]' },
]

const isReady = ref(false)
onMounted(() => { isReady.value = true })
</script>

<template>
  <div>
    <div class="hero-container mx-auto w-full flex flex-col justify-between items-center overflow-hidden select-none">
      
      <div class="mx-auto w-full max-w-[1200px] flex-1 min-h-0 p-4 sm:p-8 flex flex-col-reverse md:flex-row justify-center md:justify-between items-center gap-4 sm:gap-6 md:gap-8">
        
        <div class="flex-none md:flex-1 w-full md:w-auto h-auto min-h-[80px] sm:min-h-[120px] flex flex-col justify-center text-center md:text-left px-2">
            <vue-typewriter-effect 
                v-show="isReady" 
                :strings="['Hello, my name is Joe,\nI am a web developer']" 
            />
        </div> 

        <div class="flex justify-center items-center shrink min-h-0">
          <div class="circle-image rounded-full border-2 sm:border-4 border-white transition-all duration-300 ease-in-out"></div>   
        </div>
      </div>
          
      <div class="w-full bg-default py-4 sm:py-6 px-4 z-10 shrink-0 border-t border-gray-800">
        <div class="w-full max-w-4xl mx-auto">
            <UCarousel
                v-slot="{ item }"
                :items="techStack"
                loop
                :auto-scroll="{ speed: 0.7, stopOnInteraction: true}"
                :ui="{
                    container: 'ms-0',
                    item: 'basis-1/3 sm:basis-1/5 md:basis-1/8 px-2 sm:px-3 justify-center'
                }"
            >
            <div class="group flex flex-col items-center justify-center p-2 sm:p-4 w-full h-20 sm:h-24 rounded-xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900 cursor-pointer shadow-sm hover:shadow-md hover:border-primary-500 transition-all duration-300 ease-out">
              <UIcon 
                :name="item.icon" 
                :class="['w-8 h-8 sm:w-10 sm:h-10 transition-all duration-300 ease-out group-hover:scale-125 group-hover:-translate-y-1 group-hover:rotate-6', item.color, 'text-gray-400']" 
              />
              <span class="text-[10px] sm:text-xs font-medium mt-1 sm:mt-2 text-gray-500 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-gray-100 transition-colors duration-200">{{ item.name }}</span>
            </div>
          </UCarousel>
        </div>
      </div>

    </div>
  </div>
</template>

<style scoped>
.hero-container {
  height: calc(100vh - 57px);
  height: calc(100dvh - 57px);
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), 
    url('~/assets/images/coding-image.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
}

:deep(.Typewriter__wrapper),
:deep(.Typewriter__cursor) {
  font-size: clamp(20px, 5vw, 40px);
  white-space: pre-line;
  line-height: 1.3;
}

.circle-image {
  width: min(300px, 35vh);         
  height: min(300px, 35vh);        
  background-image: url('https://picsum.photos/400'); 
  background-size: cover;
  background-position: center;
}

@media (max-width: 768px) {
  .circle-image {
    width: min(150px, 22vh);                  
    height: min(150px, 22vh);
  }
}

@media (max-width: 480px) {
  .circle-image {
    width: min(120px, 18vh);                  
    height: min(120px, 18vh);
  }
}
</style>
