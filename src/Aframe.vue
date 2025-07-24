<script setup>
  import { ref } from 'vue';
  import TheScene from './components/TheScene.vue';

  const scale = ref(1);
  const loaded = ref(true);
</script>

<template>
  <TheScene
    @loaded="loaded = true"
  />
</template>