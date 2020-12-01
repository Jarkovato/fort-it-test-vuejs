<template>
  <div id="app">
    <search-list/>
  </div>
</template>

<script>
import SearchList from './components/SearchList'
export default {
  name: 'App',
  components: {
    SearchList
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  background-color: #f9f9fa;
  height: 100vh;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 60px 0px;
  background-color: #f9f9fa;
  min-height: 100vh;
}
</style>
