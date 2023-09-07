<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header class="flex justify-between align-center main-header">
    <img alt="Vue logo" class="logo" src="logo.png" width="200" />

    <div class="flex justify-around align-center my-4 mr-10 wrapper">
      <nav class="text-xl">
        <RouterLink to="/" class="ml-4">Home</RouterLink>
        <RouterLink to="/list" class="ml-4">List</RouterLink>
        <a href="#" class="ml-4">Stuff</a>
        <RouterLink to="/about" class="ml-4">About</RouterLink>
      </nav>
    </div>
  </header>
  <main class="main-container">
  <RouterView />
  </main>
  <footer class="flex justify-around align-center main-footer">
    <img src="logofooter.png" alt="BentriList" width="100"/>
    <div class="flex justify-between align-center my-4">
      <a class="ml-2" href="">Home</a>
      <a class="ml-2" href="">List</a>
      <a class="ml-2" href="">Stuff</a>
      <a class="ml-2" href="">About</a>
    </div>
  </footer>

</template>

<style scoped>
.main-header, .main-footer{
  background-color: #202020;
  color: #FFFFFF;
}
.main-container{
  min-height: 100vh;
}
</style>
