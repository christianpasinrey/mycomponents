<script setup lang="ts">
  import {defineAsyncComponent} from 'vue'

  const HeroSection = defineAsyncComponent(() => import('./components/HeroSection.vue'))
</script>

<template> 
  <header>
   
  </header>

  <main>
    <HeroSection />
  </main>
</template>

<style scoped>

</style>
