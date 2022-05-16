<script setup>
import { ref } from 'vue'

</script>

<template>
  <header>
    <h1>New Transaction</h1>
  </header>
  <main>
    <div class="form form--transfer">
    <div class="form__row">
      <label for="username">Receiver</label>
      <input type="text" id="username" name="username" placeholder="Username">
    </div>
        <div class="form__row">
      <label for="amount">Amount</label>
      <input type="number" id="amount" name="amount" placeholder="£ 100">
    </div>
        <div class="form__row">
      <label for="message">Receiver</label>
      <input type="text" id="message" name="message" placeholder="Type something here">
    </div>

    <div class="form__row">
      <label for="password">Password</label>
      <input type="password" id="password" name="password" placeholder="Confirm your password">
    </div>
    <button type="submit" class="button">Login</button>
  </div>
  </main>
</template>

<style scoped>
a {
  color: #42b983;
}
</style> 
