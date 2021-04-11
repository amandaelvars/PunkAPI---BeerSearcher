<template>
  <div id="app">
    <div class = "header">
      <Index msg="BEER-SEARCHER"/>
    </div>
  </div>
</template>

<script>
import Index from './components/index.vue'

export default {
  name: 'App',
  components: {
    Index
  }
}
</script>

<style>
#app {
  font-family:Arial, Helvetica, sans-serif;
  font-weight: bold;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}
.header{
  background-image: url('./assets/beerbackground.jpeg');
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent
}

h1{
  font-size: 80px;
}
p{
  font-size:14px;
  color:black;
  font-weight: normal;
}
button{
  cursor:pointer;
  height: 24px;
  background-color:antiquewhite;
  font-family: Arial, Helvetica, sans-serif;
  font-size:14px;
  border:none;
  border-radius:5px;
}
button:hover{
  box-shadow: 2px 2px rgba(0,0,0,0.4);
  cursor:pointer;
}
</style>
