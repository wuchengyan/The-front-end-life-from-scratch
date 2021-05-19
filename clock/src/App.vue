<template>
  <div id="app">
    <clock />
  </div>
</template>

<script>
import clock from './components/clock.vue';
export default {
  components: { clock },
  name: "App",
};
</script>

<style scoped>
#app {
  background: #0f3854;
  background: radial-gradient(ellipse at center, #0a2e38 0%, #000000 70%);
  background-size: 100% 100%;
  height: 100%;
  position: fixed;
  width: 100%
}
</style>
