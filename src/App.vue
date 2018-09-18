<template>
  <div id="app">
    <nav>
      <router-link to="/" >Home</router-link>
      <router-link to="/about">About</router-link>
    </nav> 
     <router-view/>
     <skills/>
     <!-- <about/> -->
   </div>
</template>

<script>
import Skills from './components/Skills.vue'

export default {
  name: 'app',
  components: {
    Skills
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
@import url(https://fonts.googleapis.com/css?family=Monsterrat:400,700);
body{
  background-color: #EEEEEE;
  font-family:'montserrat',sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  /* align-items: center; */
  padding-top: 50px;

}
body,html{
  margin:0;
  height: 100%;
}
#app{
  width: 50%;
}
nav{
  padding: 20px 20px 20px 0;
}
nav a{
  padding: 10px;
  text-decoration: none;
  background: #ffffff;
  border-radius: 3px;
  color: blue;
  font-weight: bold;
  margin-right: 15px;
}
</style>
