<script setup>
import { ref, onMounted } from 'vue'

let user = ref({});

function login() {
  let btnLogin = document.querySelector(".button--login").addEventListener("click", function () {
    console.log("clicked");
    let username = document.querySelector("#username").value;
    let password = document.querySelector("#password").value;

    fetch("http://localhost:3002/api/v1/users/login", {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify({
        username: username,
        password: password
      })
    })
      .then(response => response.json())
      .then((json) => {
        user.value = {
          username: username,
          password: password
        };
        if (json.status === "Success") {
          let token = json.data.token;
          localStorage.setItem("token", token);

          window.location.href = "#/home";
        } else {
          let feedback = document.querySelector(".alert");
          feedback.textContent = "Log in failed";
          feedback.classList.remove("hidden");
          feedback.style.backgroundColor = "red";
        }
      })
      .catch(error => console.log(error));
  });
}

onMounted(() => {
  login();
});

</script>

<template>
  <main>
    <h1>Welcome to Jackpot</h1>
    <div class="form form--login">
      <h2>Login</h2>
      <div class="alert hidden">
        Here is some feedback
      </div>
      <div class="form__row">
        <label for="username">Username</label>
        <input type="text" id="username" name="username" placeholder="Username">
      </div>
      <div class="form__row">
        <label for="password">Password</label>
        <input type="password" id="password" name="password" placeholder="Password">
      </div>
      <button class="button button--login">Log in</button>
      <p>
        Don't have an account yet? | <a href="#/register">Register</a>
      </p>
    </div>
  </main>
</template>

<style scoped>
a {
  color: #42b983;
}

.hidden {
  display: none;
}

.alert {
  margin-top: 1em;
  background-color: #B4C4E7;
  padding: 0.5em;
  margin-bottom: .5em;
  color: #32549d;
}
</style>
