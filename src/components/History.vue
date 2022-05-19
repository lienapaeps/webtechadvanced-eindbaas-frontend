<script setup>
import { ref, onMounted } from 'vue'

let transfers = ref([]);

function addHistory() {
  fetch("http://localhost:3001/api/v1/transfers")
    .then(response => response.json())
    .then((data) => {
      console.log(data.data.transfers);
      transfers.value = data.data.transfers;
      transfers.value.filter(transfer => {
        if (transfer.amount <= 0) {
          document.querySelector(".card--transfer").style.backgroundColor = "green";
        } else {
          document.querySelector(".card--transfer").style.backgroundColor = "#44A06F";
        }
      });
    })
    .catch(error => console.log(error));
}

onMounted(() => {
  addHistory();
});


</script>

<template>
  <header>
    <h1>History</h1>
  </header>
  <main class="main--history">
    <div class="card card--transfer" v-for="t, index in transfers" v-bind:key="index">
      <div class="card__item transfer__date">{{ t.time }}</div>
      <div class="card__item transfer__sender">{{ t.sender }}</div>
      <div class="card__item transfer__amount"><span>£</span>{{ t.amount }}</div>
      <div class="card__item transfer__message">{{ t.message }}</div>
    </div>
  </main>
  <nav></nav>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
