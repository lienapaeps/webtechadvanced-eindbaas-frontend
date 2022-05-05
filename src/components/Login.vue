<script setup>
import { ref } from 'vue'

</script>

<template>
  <main>
    <h1>Welcome to Jackpot</h1>
    <div class="form form--login">
      <h2>Login</h2>
      <div class="form__row">
        <label for="username">Username</label>
        <input type="text" id="username" name="username" placeholder="Username">
      </div>
      <div class="form__row">
        <label for="password">Password</label>
        <input type="password" id="password" name="password" placeholder="Password">
      </div>
      <button type="submit" class="button">Login</button>
      <p>
        Don't have an account yet? | <a href="#">Register</a>
      </p>
    </div>
  </main>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
