<script setup>
import { ref, onMounted } from 'vue'

let transfer = ref({});

function sendTransfer() {
  document.querySelector(".button--transfer").addEventListener("click", function () {
    console.log("clicked");
    let receiver = document.querySelector("#receiver").value;
    let amount = document.querySelector("#amount").value;
    let message = document.querySelector("#message").value;

    let today = new Date();
    let date = today.getFullYear() + '-' + (today.getMonth() + 1) + '-' + today.getDate();
    let time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
    let dateTime = date + ' ' + time;


    fetch("https://weareimd-jackpot.herokuapp.com/api/v1/transfers/create", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "Authorization": "Bearer " + localStorage.getItem("token")
      },
      body: JSON.stringify({
        "receiver": receiver,
        "amount": amount,
        "message": message,
        "time": dateTime
      })
    })
      .then(response => response.json())
      .then((json) => {
        transfer.value = {
          receiver: receiver,
          amount: amount,
          message: message,
          time: dateTime
        };
        if (json.status === "Success") {
          let feedback = document.querySelector(".alert");
          feedback.textContent = "Transaction successful";
          feedback.classList.remove("hidden");

          window.location.href = "#/home";
        } else {
          let feedback = document.querySelector(".alert");
          feedback.textContent = "Transaction failed";
          feedback.classList.remove("hidden");
          feedback.style.backgroundColor = "red";
        }
      })
      .catch(error => {
        console.log(error);
        // redirecten naar log in
       // window.location.href = "/";
        // token verwijderen
      });
  });
}

onMounted(() => {
  sendTransfer();
});

</script>

<template>
  <main>
    <h1>New Transaction</h1>
    <div class="form form--transfer">
      <div class="alert hidden">
        Here is some feedback
      </div>
      <div class="form__row">
        <label for="receiver">Receiver</label>
        <input type="text" id="receiver" name="receiver" placeholder="Username receiver">
      </div>
      <div class="form__row">
        <label for="amount">Amount</label>
        <input type="number" id="amount" name="amount" placeholder="£ 100">
      </div>
      <div class="form__row">
        <label for="message">Message</label>
        <input type="text" id="message" name="message" placeholder="Type something here">
      </div>
      <button class="button button--transfer">Send</button>
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
