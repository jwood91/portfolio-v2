<script>
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
    setup() {
        
    },
})
</script>

<template>
<div class="hero-container">
    <div class="hero-content-container">
        <h1 class="font-bold text-blue-600"> Hello, my name is Joe, I am a web develper </h1>
        <div class="circle-image"></div>    
    </div>    
</div>    
</template>
<style scoped>
.hero-container {
  margin: 0 auto;
  width: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  background-color: grey;
}
.hero-content-container {
  max-width: 1200px;
  height: 100vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>