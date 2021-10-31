<template>
  <div id="app">
    <AppHeader/>
    <router-view/>
  </div>
</template>

<script>
  import AppHeader from "./components/AppHeader.vue";
  export default {
    components: {
      AppHeader
    }
  }
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  a{
    text-decoration: none;
  }
  body{
    background: #767676;
  }
</style>
