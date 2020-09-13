<template>
  <div class="home">
    <Top :topMessage="topMessage" :activeCard="activeCard" />
    <Card :cardFull="cardFull" @removeCard="removeCard" :activeCard="activeCard" />
    <button class="remove" v-if="this.cardFull.id" @click="showPopup">Remove Card</button>
    <MyPopup :show="show" @result="alertResult" />
    <CardStack :cards="cards" @showCard="showCard" />
  </div>
</template>

<script>
import Top from '@/components/Top.vue'
import Card from '@/components/Card.vue'
import CardStack from '@/components/CardStack.vue'
import MyPopup from '@/components/MyPopup.vue'
export default {
  name: 'Home',
  data () {
    return {
      topMessage: "E-Wallet",
      activeCard: true,
      deleteResponse: false,
      show: false,
      cardFull: {
          
        }
    }
  },
  components: {
    Top,
    Card, 
    CardStack,
    MyPopup
  },
  props: {
    cards: Array
  },
  methods: {
    showCard(value) {
      this.cardFull = value;
    },
    removeCard(value) {
      this.$emit('removeCard', value)
    },
    alertResult(value) {
    this.show = false
    if(value == true) {
      this.$emit('removeCard', this.cardFull.id)
    }
  },
    showPopup() {
    this.show = true;
    }
}
}
</script>
<style scoped>
.remove {
  margin-top: 1%;
  text-decoration: none;
  padding: 0.5rem;
  border-radius: 20px;
  font-size: 1em;
  background:#ffffff;
}
</style>        