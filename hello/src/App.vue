<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:#FFFFFF;
  margin-top: 60px;
}
* {background-color: blue; color: #fff; font-weight: 1000;}
button {border-color:#fff; outline:0; color:#fff;}
input {border: none; outline: 0; color: #fff;}
input::placeholder {color:#fff};
</style>
