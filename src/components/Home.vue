<script setup>
import { ref, onMounted } from 'vue'

let transfers = ref([]);
let users = ref([]);


function recentHistory() {
  fetch("http://localhost:3002/api/v1/transfers", {
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

function getBalance() {
  fetch("https://weareimd-jackpot.herokuapp.com/api/v1/users", {
    "headers": {
      "Authorization": "Bearer " + localStorage.getItem("token")
    }
  })
    .then(response => response.json())
    .then((data) => {
      users.value = data.data.users;
    })
    .catch(error => {
      console.log(error);
      document.querySelector(".balance__number").innerHTML = `<img class="empty" src="./src/assets/wallet.png" alt="Nothing here" />`;

      // redirecten naar log in
      window.location.href = "/";
      // token verwijderen
    });
}

onMounted(() => {
  recentHistory();
  getBalance();
});
</script>

<template>
  <header>
    <h1>My wallet</h1>
  </header>
  <main>
    <div class="coin">
      <img class="coin__img" src="../assets/Vector.svg" alt="Coin">
    </div>
    <div class="balance">
      <h2 class="balance__text">Current balance</h2>
      <h3 class="balance__number">{{ users.balance }}</h3>
    </div>
    <div class="recent--transfer">
      <h2 class="card__title">Recent transactions</h2>
      <div class="card card--transfer" v-for="t, index in transfers" v-bind:key="index">
        <div class=" card__item card__date">{{ t.time }}</div>
        <div class="card__item card__sender">{{ t.sender }}</div>
        <div class="card__item card__amount"><span>£</span>{{ t.amount }}</div>
        <div class="card__item card__message">{{ t.message }}</div>
      </div>
    </div>
  </main>
  <nav></nav>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
