<script setup>
import { ref, onMounted } from 'vue';

let users = ref([]);
let username = ref('');
let balance = ref('');

function addLeader() {
  fetch("http://localhost:3001/api/v1/users")
  .then(response => response.json())
  .then((data) => {
      users.value = data.data.users;
      users.value.revers();
  })
  .catch(error => console.log(error));
}

onMounted(() => {
  addLeader();
});

</script>

<template>
  <header><h1>Leaderboard</h1></header>
  <main class="main__leaders">
    <div class="card card__leader" v-for="user, index in users" v-bind:key="index">
      <div class="card__front">
        <div class="card__item leader--rank">#</div>
        <div class="card__item leader--name">{{ user.username}}</div>
      </div>
        <div class="card__item leader--balance">{{user.balance}}</div>
    </div>
  </main>
  <nav></nav>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
