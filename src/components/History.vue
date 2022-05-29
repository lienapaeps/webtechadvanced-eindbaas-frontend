<script setup>
import { ref, onMounted } from 'vue'

let transfers = ref([]);

function addHistory() {
  fetch("https://weareimd-jackpot.herokuapp.com/api/v1/transfers", {
    "headers": {
      "Authorization": "Bearer " + localStorage.getItem("token")
    }
  })
    .then(response => response.json())
    .then((data) => {
      // console.log(data.data.transfers);
      transfers.value = data.data.transfers;
      // transfers.value.filter(transfer => {
      //   if (transfer.amount <= 0) {
      //     document.querySelector(".card--transfer").style.backgroundColor = "green";
      //   } else {
      //     document.querySelector(".card--transfer").style.backgroundColor = "#44A06F";
      //   }
      // });
    })
    .catch(error => {
      console.log(error);
      document.querySelector(".main--history").innerHTML = `<img class="empty" src="./src/assets/wallet.png" alt="Nothing here" />`;
      // redirecten naar log in
      window.location.href = "/";
      // token verwijderen
    });
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
      <div class="card__item card__date">{{ t.time }}</div>
      <div class="card__item card__sender">{{ t.sender }}</div>
      <div class="card__item card__amount"><span>£</span>{{ t.amount }}</div>
      <div class="card__item card__message">{{ t.message }}</div>
    </div>
  </main>
  <nav></nav>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
