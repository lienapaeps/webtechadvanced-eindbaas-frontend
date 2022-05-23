<script setup>
import { ref, onMounted } from 'vue';

let users = ref([]);

function addLeader() {
  fetch("http://localhost:3002/api/v1/users")
    .then(response => response.json())
    .then((data) => {
      users.value = data.data.users;
      users.value.sort(function (a, b) {
        return b.balance - a.balance;
      });
    })
    .catch(error => console.log(error));
}

onMounted(() => {
  addLeader();
});

</script>

<template>
  <header>
    <h1>Leaderboard</h1>
  </header>
  <main class="main--leaders">
    <div class="card card--leader" v-for="user, index in users" v-bind:key="index">
      <div class="card__front">
        <div class="card__item leader__rank">#</div>
        <div class="card__item leader__name">{{ user.username }}</div>
      </div>
      <div class="card__item leader__balance"><span>£</span>{{ user.balance }}</div>
    </div>
  </main>
  <nav></nav>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
