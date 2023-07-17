<template>
  <section class="clear" id="clrBtn">
    <button @click="this.$emit('clear')">不玩了</button>
  </section>
</template>

<script>
export default {
  props: {
    gameList: Array
  },
  emits: ['clear']
}
</script>