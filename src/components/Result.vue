<template>
  <main class="result">
    <p v-for="msg in gameList">{{ msg }}</p>
  </main>
</template>

<script>
export default {
  props: {
    gameList: Array
  }
}
</script>