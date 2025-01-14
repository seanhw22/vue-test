<template>
  <HeaderDefault />
  <div class="container">
    <SideMenu />
    <MainContent />
  </div>
</template>

<script>
import HeaderDefault from './components/header.vue'
import SideMenu from './components/SideMenu.vue'
import MainContent from './components/main.vue'

export default {
  name: 'App',
  components: {
    HeaderDefault,
    SideMenu,
    MainContent
  },
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
}

body {
  height: 100vh;
}

.container {
  display: flex;
  margin: 0;
  padding: 0;
  max-width: 100%;
  width: 100%;
  min-height: calc(100vh - 70px);
  box-sizing: border-box;
}
</style>
