<script setup>
import { ref, onMounted } from 'vue'

let user = ref({});

function logout() {
    localStorage.clear();
    window.location.href = "/";
}

onMounted(() => {
  logout();
});

//create routes object

</script>

<template>
  <main>
      <p>Logging out...</p>
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
