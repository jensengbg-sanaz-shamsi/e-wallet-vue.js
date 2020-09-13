<template>
  <article v-if="cardFull.id" class="card" :cardFull="cardFull" :class="cardFull.vendor">
    <header class="header">
      <img src="@/assets/chip-light.svg" alt="chip" />
      <img
        v-if="cardFull.vendor"
        :src="require('@/assets/vendor-' + cardFull.vendor + '.svg')"
        :alt="cardFull.vendor"
      />
    </header>
    <section class="number" v-if="cardFull.cardnumber">
      <h1>
        {{splitString}}
        <br />
      </h1>
    </section>
    <section class="info">
      <aside class="holder">
        <span>Cardholder:</span>
        <p>{{cardFull.cardholder}}</p>
      </aside>
      <aside class="valid">
        <span>Valid thru:</span>
        <p>{{cardFull.expmonth}}/{{cardFull.expyear}}</p>
      </aside>
    </section>
  </article>
</template>  
<script>
export default {
  name: "Card",
  props: {
    cardFull: Object,
    activeCard: Boolean,
  },
  data () {
    return {
  }
  },
  computed: {
    splitString(){
      let spaceNum = this.cardFull.cardnumber;
      let ccNumSpaces = spaceNum.match(/.{1,4}/g);
      return ccNumSpaces.join("-");
    }
  }
}
</script>
<style scoped>
.card {
  width: 24rem;
  height: 14rem;
  border-radius: 0.6rem;
  padding: 1rem;
  box-sizing: border-box;
  display: grid;
  gap: 0.5rem 0;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: 3rem;
  font-size: 1.2rem;
}
h1 {
  font-size: 1.4rem;
  margin-block-start: -0.3em;
  margin-block-end: 2em;
}
.number {
  grid-column: auto / span 2;
  grid-row: auto / span 1;
  display: flex;
  font-size: 1.4rem;
  letter-spacing: 0.05rem;
  padding: 0.5rem 0 0 0;
  text-transform: uppercase;
}
.card section.info {
  display: flex;
  grid-column: auto / span 2;
  grid-row: auto / span 1;
}
article {
  margin: 0 auto;
  background:#222;
  color: #eee;
}
.card section aside span {
  display: block;
  text-transform: uppercase;
  font-size: 0.7rem;
  margin: 0 0 0.25rem;
}
.card header {
  align-self: flex-end;
  opacity: 1;
  display: flex;
  grid-column: auto / span 2;
  grid-row: auto / span 2;
  justify-content: space-between;
  align-items: flex-start;
}
.card section aside p {
  display: block;
  text-transform: uppercase;
  margin: 0;
  padding: 0;
}
.card section aside.valid span {
  text-align: right;
}
.card section aside.valid p {
  text-align: right;
}
aside {
  display: block;
}
.holder {
  flex: 1;
}
header {
  display: block;
}
.header {
  display: flex;
  grid-column: auto/span 2;
  grid-row: auto/span 2;
  justify-content: space-between;
  align-items: flex-start;
}
.bitcoin {
  background: linear-gradient(
      0.689turn,
      hsla(0, 0%, 100%, 0.15),
      hsla(0, 0%, 100%, 0) 99.07%
    ),
    #ffae34;
  color: #222;
}
.evil {
  background: linear-gradient(248.3deg, rgba(0, 0, 0, 0.16), transparent),
    #f33355;
  color: #fff;
}
.ninja {
  background: linear-gradient(
      248.3deg,
      hsla(0, 0%, 100%, 0.15),
      hsla(0, 0%, 100%, 0)
    ),
    #222;
  color: #fff;
}
.blockchain {
  background: linear-gradient(248.52deg, rgba(0, 0, 0, 0.15) 1.49%, transparent),
    #8b58f9;
  color: #fff;
}
</style>