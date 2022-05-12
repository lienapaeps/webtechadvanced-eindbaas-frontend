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
console.log(currentPath + " is the current path");

// computed properties are derived from other variables, this will return the name of a component 
let currentView = computed(() => 
  routes[currentPath.value.slice(1) || '/'] || Home);
console.log(currentView);

onMounted( () => {
  window.addEventListener('hashchange', () => {
    currentPath.value = window.location.hash;
  })
});

</script>
<template>
  <div id="app">
    <a class="toHome" href="#/home"><img src="./assets/arrow-left.svg" alt="back"></a>
    <a href="#/login" class="logout"><img src="./assets/logout.svg" alt="logout"></a>
          <component :is="currentView" />
    <div class="nav">
      <a class="navlink " href="#/history"><img src="./assets/time-history.svg" alt="history"><span>History</span></a>
      <a class="toSend" href="#/Send"><img src="./assets/send.svg" alt="send"></a>
      <a class="navlink" href="#/leader"><img src="./assets/cup.svg" alt="cup"><span>Leaderboard</span></a>
    </div>

  </div>
</template>
<style>
/* @import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.1/font/bootstrap-icons.css"); */

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.nav {
  display: grid;
  position: absolute;
  bottom: 0;
  width: 100%;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  justify-items: space-around;
  align-items: center;
  border-top: 1px solid #2c3e50;
  padding: 1em 1em;
}

.toSend {
  width: 100%;
  height: 100%;
}

.navlink {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: .8em;
  color: #2c3e50;
  text-decoration: none;
}

.navlink img {
  width: 32px;
  height: 32px;
  margin: 8px;
}
</style>
