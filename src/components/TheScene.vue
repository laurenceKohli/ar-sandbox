<script setup>
  import { ref } from 'vue';

  const allAssetsLoaded = ref(false);

</script>

<template>
  
  <a-scene
    embedded arjs
  >
    
    <a-assets @loaded="allAssetsLoaded = true">
    </a-assets>

    <template v-if="allAssetsLoaded">
    <a-marker preset='hiro'>
      <a-box position='0 0.5 0' material='opacity: 0.5;'></a-box>
		</a-marker>

    <a-marker-camera >
      <a-box position='0 0.5 0' material='opacity: 0.5;'></a-box>
		</a-marker-camera>
    <!--   <a-box color="red"></a-box>

      
    <a-box color="green"
      id="grille-2"
      position="-0.56 0 0"
      scale="2 0.1 2"
      ></a-box> -->
      
    </template>

  </a-scene>
</template>