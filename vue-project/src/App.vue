<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue';
</script>

<!-- Challenge: Make a box with an image and a text -->

<template>
  <Header />
  <RouterView />
</template>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap');

  #app {
    font-family: "Nunito", sans-serif;
  }
</style>