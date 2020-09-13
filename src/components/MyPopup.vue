<template>
  <section v-if="show" class="popup">
    <div id="wrapper">
      <h1>Are you sure you want to delete the card?</h1>
      <button id="cancel" @click="cancel">No</button>
      <button @click="accept">Yes</button>
    </div>
  </section>
</template>
<script>
export default {
  name: "MyPopup",
  data () {
    return {
      popupresult: Boolean,
    }
  },
  props: {
    show: Boolean
  }, methods: {
    cancel() {
      this.popupresult = false;
      this.$emit('result', this.popupresult)
    },
    accept() {
      this.popupresult = true;
      this.$emit('result', this.popupresult)
    }
  }
}
</script>
<style scoped>
.popup {
  backdrop-filter: blur (2px);
  background: rgba(61, 61, 61, 0.897);
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}
#wrapper {
  background: linear-gradient(
      248.3deg,
      hsla(0, 65%, 34%, 0.287),
      hsla(0, 32%, 36%, 0.582)
    ),
    #222;
  color: rgb(255, 255, 255);
  position: fixed;
  left: 50%;
  right: 50%;
  top: 25%;
  transform: translateX(-50%);
  width: 250px;
  border: 2px solid rgb(255, 255, 255);
  width: 400px;
  z-index: 100000;
  font-size: 2rem;
}
#cancel {
  border: 0.125rem solid red;
}
button {
  display: inline-block;
  height: 2rem;
  width: 6rem;
  font-size: 1.2rem;
  text-transform: uppercase;
  font-weight: 700;
  text-decoration: none;
  color: #000;
  border: 0.125rem solid green;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  border-radius: 0.5rem;
  margin: 2rem 2%;
}
</style>