<script setup>
  import { ref, onMounted } from 'vue';

  const allAssetsLoaded = ref(false);
  const arSystemReady = ref(false);

onMounted(() => {
  const scene = document.querySelector('a-scene');
  if (scene) {
    if (scene.hasLoaded) {
      arSystemReady.value = true;
    } else {
      scene.addEventListener('loaded', () => {
        arSystemReady.value = true;
      });
    }
  }
});
</script>

<template>
  
  <a-scene
    vr-mode-ui="enabled: false;"
    renderer="logarithmicDepthBuffer: true;"
    embedded
    arjs="debugUIEnabled: true; sourceType: webcam; markersAreaEnabled: true;"
  >
    
    <a-assets @loaded="allAssetsLoaded = true">
    </a-assets>

    <template v-if="allAssetsLoaded && arSystemReady">
    <a-marker preset='hiro'>
      <a-box position='0 0.5 0' material='opacity: 0.5;'></a-box>
		</a-marker>

    <a-marker-camera >
      <!-- <a-box position='0 0.5 0' material='opacity: 0.5;'></a-box> -->
		</a-marker-camera>

    <a-nft
      type="nft"
      url="./aframe-vue-boilerplate/assets/pinball"
      smooth="true"
      smoothCount="10"
      smoothTolerance=".01"
      smoothThreshold="5"
    >
      <a-box position="0 0 0" scale="20 20 20" color="red"></a-box>
    </a-nft>

    <!-- <a-nft
      type="nft"
      url="./aframe-vue-boilerplate/testAR-Suisse-colors"
      smooth="true"
      smoothCount="10"
      smoothTolerance=".01"
      smoothThreshold="5"
    >
      <a-box position='0 0.5 0' material='opacity: 0.5;'></a-box>
    </a-nft> -->
    <!--   <a-box color="red"></a-box>

      
    <a-box color="green"
      id="grille-2"
      position="-0.56 0 0"
      scale="2 0.1 2"
      ></a-box> -->
      
    </template>

  </a-scene>
</template>