<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import Login from './components/Login.vue'
import Home from './components/Home.vue'
import Leader from './components/Leader.vue'
import Send from './components/Send.vue'
import History from './components/History.vue'

import { ref, computed, onMounted } from 'vue'

//create routes object
const routes = {
  '/': Login,
  '/home': Home,
  '/leader': Leader,
  '/send': Send,
  '/history': History
}

//get hash from url
let currentPath = ref(window.location.hash);
// console.log(currentPath + " is the current path");

// computed properties are derived from other variables, this will return the name of a component 
let currentView = computed(() => 
  routes[currentPath.value.slice(1) || '/'] || Home);
// console.log(currentView);

onMounted( () => {
  window.addEventListener('hashchange', () => {
    currentPath.value = window.location.hash;
  })
});

</script>
<template>
  <div id="app">
    <div class="nav nav--top">
      <a class="top__link toHome" href="#/home"><img class="nav__icon" src="./assets/arrow-left.svg" alt="back"></a>
      <a class="top__link logout" href="#/login"><img class="nav__icon" src="./assets/logout.svg" alt="logout"></a>
    </div>
          <component :is="currentView" />
    <div class="nav nav--bottom">
      <a class="nav__link " href="#/history"><img class="nav__icon" src="./assets/time-history.svg" alt="history"><span>History</span></a>
      <a class="icon--send" href="#/send"><img src="./assets/send.svg" alt="send"></a>
      <a class="nav__link" href="#/leader"><img class="nav__icon" src="./assets/cup.svg" alt="cup"><span>Leaderboard</span></a>
    </div>

  </div>
</template>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
