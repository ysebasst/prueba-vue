<template>
  <!-- <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div> -->
  <main>
    <Navbar />
    <router-view />
  </main>
</template>

<script>
import Navbar from '@/components/Navbar'

export default {
  components:{
    Navbar
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: #999;
}
</style>
