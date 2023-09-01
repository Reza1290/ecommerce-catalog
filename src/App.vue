<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import ViewPage from './components/ViewPage.vue';
import HomePage from './components/HomePage.vue';
import ErrorPage from './components/ErrorPage.vue';
import Vue from 'vue';
import VueRouter from 'vue-router';




Vue.use(VueRouter)



const routes = [
    { path: '/', component: HomePage },
    { path: '/view/:id?', component: ViewPage },
    { path: '/unavailable', component: ErrorPage}
    // { path: '/*', {window.location="/"}} 
]

const router = new VueRouter({
    mode: 'history',
    routes
})

export default {
  router,
  name: 'App',
  //   components: {
  //     HomePage
  // }
}
</script>

<style>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* color: #2c3e50; */
  height: 100vh;
  background-color: white;
}

.flex{
  display: flex;
}

*{
  margin: 0;
}
</style>
