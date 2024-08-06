<script setup lang="ts">
  import {defineAsyncComponent} from 'vue'

  const CardComponent = defineAsyncComponent(() => import('./components/CardComponent.vue'))
</script>

<template> 
  <header>
   
  </header>

  <main>
    <CardComponent 
      upperTitle
      upperSubtitle
    />
  </main>
</template>

<style scoped>

</style>
