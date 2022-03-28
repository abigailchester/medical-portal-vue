<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <MedPortal />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import MedPortal from './components/MedPortal.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    MedPortal
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

#app {
  font-family: Helvetica, sans-serif;
  font-size: small;
  background-color: #BECEF5;
  min-height: 100vh;
  line-height: 1.7;
}

.el-input__inner {
  padding: 0 7px;
}
.el-input--suffix .el-input__inner {
  padding: 0 5px;
}

</style>
