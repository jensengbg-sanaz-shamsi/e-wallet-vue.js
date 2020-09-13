<template>
  <div class="AddCard">
    <Top :topMessage="topMessage" />
    <Card :cardFull="cardFull" />
    <CardForm v-bind:cards="cards" @addCard="addCard" />
  </div>
</template>
<script>
import Top from '@/components/Top.vue'
import Card from '@/components/Card.vue'
import CardForm from '@/components/CardForm.vue'
export default {
    name: "AddCard",
    props: {
      cards: Array
    },
    components: {
      Top,
      Card,
      CardForm
    },
    data () {
      return {
        topMessage: "Add new card",
        cardFull: {
          id: "X", cardnumber: "XXXXXXXXXXXXXXXX", cardholder: "Firstname Lastname", expyear: "XX", expmonth: "XX", ccv: "XXX", vendor: ""
        }
      }
    }, 
    methods: {
      addCard(value) {
        this.cardFull = value.card;
        if(this.cardFull.id == "") {
        this.cardFull.id = this.$props.cards.length + 1;
        } 
        let checkExisting = this.$props.cards.find((card) => card.id == this.cardFull.id)
        if(typeof(checkExisting) == 'undefined' && value.event.type == 'click') {
          this.$emit('addCard', this.cardFull)
        } 
    }
    }
}
</script>