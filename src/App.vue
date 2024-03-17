<script setup>
  import {RouterView} from 'vue-router'


</script>

<template>
  <main class="container">
    <header>
      <h1>Head in app.vue</h1>
    </header>
    <RouterView/>
  </main>
</template>

<style scoped>
.container{
  max-width: 1200px;
  margin: auto;
}
</style>