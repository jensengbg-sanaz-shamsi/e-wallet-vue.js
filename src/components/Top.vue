<template>
  <header class="top">
    <h1>{{message}}</h1>
    <h3 v-if="this.$props.activeCard == true">Active Card</h3>
  </header>
</template>
<script>
export default {
  props: {
    topMessage: String,
    activeCard: Boolean
  },
  data () {
    return {
      message: this.$props.topMessage
    }
  }
}
</script>
<style scoped>
</style>