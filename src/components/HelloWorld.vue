<template>
  <div class="hello">
<!--    <img :src="'/assets/img/2.png'" alt="">-->
    <img alt="Vue logo" :src="getImage(firstDice)">
    <img alt="Vue logo" :src="getImage(secondDice)">
    <button @click="rollDice">SALLA</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  data() {
    return {
      firstDice: Math.floor(Math.random() * 6) + 1,
      secondDice: Math.floor(Math.random() * 6) + 1,
    };
  },
  methods: {
    getImage(diceNumber) {

      return require("../assets/" + diceNumber + ".png");
    },
    rollDice() {
      this.firstDice = Math.floor(Math.random() * 6) + 1;
      this.secondDice = Math.floor(Math.random() * 6) + 1;
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
