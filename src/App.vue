<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Calculator from './components/Calculator.vue'
import Navbar from './components/Navbar.vue'
</script>

<template>
    <Navbar/>
    <Calculator/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  
}

* {
  background-color: rgba(39, 38, 38, 0.9);
}

</style>
