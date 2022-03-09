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

@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');


#app {
  font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #121213;
  margin-top: 60px;
  font-size: 32px;
  
}
</style>
