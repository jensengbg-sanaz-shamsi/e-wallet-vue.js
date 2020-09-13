<template>
  <section id="cardStack">
    <Card
      v-for="card in cards"
      :key="card.id"
      :cardFull="card"
      @removeCard="removeCard"
      @click.native="showCard(card.id)"
    ></Card>
  </section>
</template>
<script>
import Card from '@/components/Card.vue'
export default {
  name: "CardStack",
  props: {
    cards: Array
  },
  data () {
    return {
  }
},
    components: {
      Card
    },
    methods: {
      showCard(id) {
        let cardFull = this.$props.cards.find((card) => card.id == id) 
        this.$emit('showCard', cardFull)
      },
      removeCard(value) {
      this.$emit('removeCard', value)
    }
    }
}
</script>
<style scoped>
#cardStack {
  margin: 2rem 0 12rem;
  display: grid;
  grid-auto-rows: 4rem;
}
</style>