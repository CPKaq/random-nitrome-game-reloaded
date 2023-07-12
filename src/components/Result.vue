<template>
  <p v-for="msg in gameList">{{ msg }}</p>
</template>

<script>
export default {
  props: {
    gameList: Array
  }
}
</script>