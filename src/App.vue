<template>
  <div id="app">
    <clock/>
    <hr>
    <elapser/>
    <hr>
    <timer/>
  </div>
</template>

<script>
import Clock from './components/Clock.vue'
import Elapser from "@/components/Elapser";
import Timer from "@/components/Timer"

export default {
  name: 'App',
  components: {
    Clock,
    Elapser,
    Timer
  }
}
</script>

<style lang="scss">
:root {
  --white-text: #fff;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

body {
  background-color: #060606;
}
</style>
