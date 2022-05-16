<script setup>
import { ref } from 'vue'

</script>

<template>
<<<<<<< HEAD
  <main>
    <h1>Welcome to Jackpot</h1>
    <div class="form form--login">
      <h2>Sign up</h2>
      <div class="form__row">
        <label for="username">Username</label>
        <input type="text" id="username" name="username" placeholder="Username">
      </div>
      <div class="form__row">
        <label for="email">Email</label>
        <input type="email" id="email" name="email" placeholder="Email">
      </div>
      <div class="form__row">
        <label for="password">Password</label>
        <input type="password" id="password" name="password" placeholder="Password">
      </div>
            <div class="form__row">
        <label for="password2">Password</label>
        <input type="password" id="password--confirm" name="password2" placeholder="Confirm Password">
      </div>
      

      <button type="submit" class="button">Sign up</button>
      <p>
        Already have an account? | <a href="/">Login</a>
      </p>
    </div>
  </main>
</template>

<style scoped>
a {
  color: #42b983;
=======
    <main>
        <h1>Welcome to Jackpot</h1>
        <div class="form form--register">
            <h2>Register</h2>
            <div class="form__row">
                <label for="username">Username</label>
                <input v-model="username" type="text" id="username" name="username" placeholder="Username">
            </div>
            <div class="form__row">
                <label for="password">Password</label>
                <input v-model="password" type="password" id="password" name="password" placeholder="Password">
            </div>
            <button type="submit" class="button">Register</button>
            <p>
                Already have an account? | <a href="#">Log in</a>
            </p>
        </div>
    </main>
</template>

<script>
export default {
    name: 'Register',
    data() {
        return {
            username: '',
            password: ''
        }
    },
    methods: {
        register() {
            console.log(data);
        }
    }
}
</script>

<style scoped>
a {
    color: #42b983;
>>>>>>> 958027f06c6ff822ea51568f7bb5cc79df168afb
}
</style>
