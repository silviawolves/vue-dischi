<template>
  <div id="app">
    
    <TheHeader />
    
    <div class="container">
      <div v-if="loading" class="text-white fs-6 fw-light mt-3 mb-0 text-center">Loading...</div>
    </div>
    
    <TheMain />
    
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import TheMain from './components/TheMain.vue';
import { state } from './store.js'

export default {
  name: 'App',
  components: { TheHeader, TheMain },
  computed: {
    loading() {
      return state.loading
    }
  }
}
</script>

<style lang="scss">
@import "./assets/scss/_variables.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  background-color: $secondary;
}
</style>
