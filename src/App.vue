<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/AddCard">Add Credit Card</router-link>
    </div>
    <router-view :cards="cards" @addCard="addCard" @removeCard="removeCard" />
  </div>
</template>
<script>
export default {
  name: "App",
  data () {
    return {
      cards:[]
    }
  }, 
  methods: {
    addCard(value) {
    this.cards.push(value);
    }, 
    removeCard(id) {
      console.log(id);
      this.cards.splice(id - 1, 1)
      for(let i = 0; i < this.cards.length; i++) {
        this.cards[i].id = i + 1
        console.log(this.cards[i].id)
      } 
      location.reload();
    }
  }, 
  watch: {
    cards: {
      handler() { 
      console.log('Cards changed!');
      localStorage.setItem('cards', JSON.stringify(this.cards));
      },
      deep: true,
    },
  }, mounted() {
    console.log('App mounted!');
    if (localStorage.getItem('cards')) {
      this.cards = JSON.parse(localStorage.getItem('cards'));
      }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>