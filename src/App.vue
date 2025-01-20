<script>
import MapComponent from "@/components/MapComponent.vue";

export default {
  components: {
    MapComponent,
  },
};
</script>

<template>
  <div id="app">
    <h1>AgroMap</h1>
    <h2>Conheça um pouco sobre as principais características agrícolas de cada região do país:</h2>
    <MapComponent />
  </div>
</template>