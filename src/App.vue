<script setup lang="ts">
  import {defineAsyncComponent} from 'vue'

  const CardComponent = defineAsyncComponent(() => import('./components/CardComponent.vue'))

  const htmlCardContent = `
    <h1>This is a custom html content</h1>
    <p>Some more content here</p>
  `;

</script>

<template> 
  <header>
   
  </header>

  <main>
    <CardComponent 
      upperTitle
      upperSubtitle
      :htmlContent="htmlCardContent"
    />
  </main>
</template>

<style scoped>

</style>
