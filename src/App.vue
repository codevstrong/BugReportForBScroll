<template>
  <div id="app">
    <keep-alive>
      <router-view />
    </keep-alive>
  </div>
</template>
<script>
import Home from "views/home/Home";
export default {
  name: "App",
  components: {
    Home
  }
};
</script>
<style>
</style>
