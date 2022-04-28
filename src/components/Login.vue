<script setup>
import { ref } from 'vue'

</script>

<template>
  <main>
    <h1>Login to Jackpot</h1>
    <div>
      <label for=""></label>
      <input type="text" id="username" name="username" placeholder="Username">
      <input type="password" id="password" name="password" placeholder="Password">
      <button type="submit">Login</button>
    </div>
    <div>
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
