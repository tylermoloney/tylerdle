<template>
<div>
  <tylerdle-main />
</div>
</template>

<script>
import TylerdleMain from './components/TylerdleMain.vue'
export default {
  name: 'App',
  components: {
    TylerdleMain
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #121213;
  margin-top: 60px;
  font-size: 32px;
  
}
</style>
