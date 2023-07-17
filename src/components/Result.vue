<template>
  <main class="result">
    <p v-for="msg in gameList">{{ msg }}</p>
  </main>
</template>

<script>
export default {
  props: {
    gameList: Array
  },
  updated() {
    window.scrollBy(0, document.documentElement.clientHeight)
  }
}
</script>