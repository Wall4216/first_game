<template>
  <div class="app">
  <img class="logo" alt="Vue logo" src="./assets/logo.png">
  <h1 class="h1">Запомни</h1>
  <p>Открой все зеленые клетки</p>
    <TheBoard/>
  </div>
</template>

<script>
import TheBoard from "@/components/Board.vue";
export default {
  name: 'App',
  components: {
    TheBoard,
  }
}
</script>

<style>
  .app {
    margin-top: 40px;
    text-align: center;
    font-family: Helvetica, sans-serif;
  }
  .logo {
    width: 150px;
  }
</style>
