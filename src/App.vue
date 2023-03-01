<script setup lang="ts">
import { onMounted } from 'vue';
import ForceGraph3D from '3d-force-graph';
import graphData from './data';

onMounted(() => {
  const Graph = ForceGraph3D()(document.getElementById('3d-graph'))
    .nodeAutoColorBy('node_type')
    .linkAutoColorBy((d) => {
      console.log(graphData.nodes[d.source]);
      return graphData.nodes[d.source].node_type;
    })
    .linkOpacity(0.5)
    .graphData(graphData);
});
</script>

<template>
  <div id="3d-graph"></div>
</template>

<style scoped>
#3d-graph {
  width: 100vw;
  height: 100vh;
  margin: 0;
}
#app {
  padding: 0;
  margin: 0;
}
</style>
