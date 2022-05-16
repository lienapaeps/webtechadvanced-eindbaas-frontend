<script setup>
import { ref, onMounted } from 'vue';

let users = ref([]);

function addLeader() {
  fetch("http://localhost:3001/api/v1/users") //kan sort parameter meegeven,  dan moet dat niet in frontend.
  .then(response => response.json())
  .then((data) => {
      users.value = data.data.users;
      users.value.sort(function(a, b) {
        return b.balance - a.balance;
      });
  })
  .catch((error) => {
    console.log(error);
    document.querySelector(".main--leaders").innerHTML = `<img class="empty" src="./src/assets/wallet.png" alt="Nothing here" />`;
    });
}

onMounted(() => {
  addLeader();
});

</script>

<template>
  <header><h1>Leaderboard</h1></header>
  <main class="main--leaders">
    <div class="card card--leader" v-for="user, index in users" v-bind:key="index">
      <div class="card__front">
        <div class="card__item card__rank">{{ index +1 }}</div>
        <div class="card__item card__name">{{ user.username}}</div>
      </div>
        <div class="card__item card__balance"><span>£</span>{{user.balance}}</div>
    </div>
  </main>
  <nav></nav>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
