<template>
  <div class="container">
    <CalculateAge />
  </div>
</template>

<script>
import CalculateAge from './components/CalculateAge.vue';

export default {
  name: 'App',
  components: {
    CalculateAge,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
}

.container {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
