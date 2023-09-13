<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header class="flex justify-between align-center main-header">
    <img alt="Vue logo" class="logo" src="logo.png" width="200" />

    <div class="flex justify-around align-center my-4 mr-10 wrapper">
      <nav class="text-xl menu-nav">
        <RouterLink to="/" class="ml-4 routelink">Home</RouterLink>
        <RouterLink to="/list" class="ml-4 routelink">List</RouterLink>
        <RouterLink to="/stuff" class="ml-4 routelink">Stuff</RouterLink>
        <RouterLink to="/about" class="ml-4 routelink">About</RouterLink>
      </nav>
    </div>
  </header>
  <main class="main-container">
  <RouterView />
  </main>
  <footer class="flex justify-around align-center main-footer">
    <img src="logofooter.png" alt="BentriList" width="100"/>
    <div class="flex justify-between align-center my-4">
      <RouterLink to="/" class="ml-2 routelink">Home</RouterLink>
      <RouterLink to="/list" class="ml-2 routelink">List</RouterLink>
      <RouterLink to="/stuff" class="ml-2 routelink" >Stuff</RouterLink>
      <RouterLink to="/about" class="ml-2 routelink">About</RouterLink>
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
.menu-nav{
  color: #6a2ada;
}
.routelink:hover{
  color: #faf02f;
}
</style>
