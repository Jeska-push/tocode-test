<template>
    <the-header />
    <the-body />
    <the-footer />

</template>

<script>
import TheHeader from './components/TheHeader.vue'
import TheFooter from './components/TheFooter.vue'
import TheBody from './components/TheBody.vue'
export default {
  name: 'App',
  components: {
    TheHeader,
    TheFooter,
    TheBody
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
