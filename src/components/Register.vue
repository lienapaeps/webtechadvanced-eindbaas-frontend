<script setup>
import { ref, onMounted } from 'vue'

let user = ref({});

<<<<<<< HEAD
=======
function register() {
    let btnRegister = document.querySelector(".button--register").addEventListener("click", function () {
        console.log("clicked");
        let username = document.querySelector("#username").value;
        let password = document.querySelector("#password").value;

        fetch("http://localhost:3002/api/v1/auth/register", {
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
                    let feedback = document.querySelector(".alert");
                    feedback.textContent = "Registration successful";
                    feedback.classList.remove("hidden");

                    let token = json.data.token;
                    localStorage.setItem("token", token);

                    window.location.href = "#/home";
                } else {
                    let feedback = document.querySelector(".alert");
                    feedback.textContent = "Registration failed";
                    feedback.classList.remove("hidden");
                    feedback.style.backgroundColor = "red";
                }
            })
            .catch(error => console.log(error));
    });
}

onMounted(() => {
    register();
});

</script>

>>>>>>> b354c10cf148381608aab4973cfb45328e52976b
<template>
    <main>
        <h1>Welcome to Jackpot</h1>
        <div class="form form--register">
            <h2>Register</h2>
            <div class="alert hidden">
                Here is some feedback
            </div>
            <div class="form__row">
                <label for="username">Username</label>
                <input v-model="username" type="text" id="username" name="username" placeholder="Username">
            </div>
            <div class="form__row">
                <label for="password">Password</label>
                <input v-model="password" type="password" id="password" name="password" placeholder="Password">
            </div>
            <button class="button button--register">Register</button>
            <p>
                Already have an account? | <a href="#/">Log in</a>
            </p>
        </div>
    </main>
</template>

<style scoped>
a {
    color: #42b983;
<<<<<<< HEAD
=======
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
>>>>>>> b354c10cf148381608aab4973cfb45328e52976b
}
</style>
