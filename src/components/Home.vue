<script setup>
import { ref } from 'vue'



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
      <h3 class="balance__number">£125</h3>
    </div>
    <div class="recent--transfer">
      <h2 class="card__title">Recent transactions</h2>
      <div class="card card--transfer">
        <div class="card__item transfer__date">Time</div>
        <div class="card__item transfer__sender">Sender</div>
        <div class="card__item transfer__amount"><span>£</span>Amount</div>
        <div class="card__item transfer__message">Message</div>
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
