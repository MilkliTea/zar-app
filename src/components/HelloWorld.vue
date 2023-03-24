<template>
  <div class="hello" v-if="!gifIsActive">
    <img alt="zar" :src="getImage(firstDice)">
    <img alt="zar" :src="getImage(secondDice)">
  </div>
  <div class="hello" v-if="gifIsActive">
    <img alt="zar" :src="getImage(0)">
    <img alt="zar" :src="getImage(0)">
  </div>
  <div id="total">
    <span>Toplam: {{ total }}</span><br>
    <span id="lucky-pic" v-if="!gifIsActive && (firstDice === secondDice)"> Çift Attın Tekrar At</span>
  </div>
  <button id="dice-button" @click="rollDice">Zarları Salla</button>
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
      showGif: false,
      total: this.firstDice + this.secondDice
    };
  },
  computed: {
    gifIsActive() {

      return this.showGif;
    },
  },
  mounted() {
    this.total = this.firstDice + this.secondDice;
  },

  methods: {
    getImage(diceNumber) {
      if (diceNumber === 0) {
        return require("../assets/zar.gif");

      }
      return require("../assets/" + diceNumber + ".png");
    },
    async rollDice() {
      this.showGif = true;
      this.firstDice = Math.floor(Math.random() * 6) + 1;
      this.secondDice = Math.floor(Math.random() * 6) + 1;

      await new Promise(resolve => setTimeout(resolve, 1200));

      this.total = this.firstDice + this.secondDice;

      this.showGif = false;
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  width: 50%;
}

ul {
  list-style-type: none;
  padding: 0;
}

#dice-button {
  font-size: 24px;
  width: 50%;
  padding: 12px 24px;
  margin-top: 15px;
  background-color: #008CBA;
  color: white;
  border: none;
  border-radius: 15%;
  cursor: pointer;
}

#lucky-pic {
  color: darkred;
}

#total {
  font-size: 24px;
  margin-top: 15px;
  font-weight: bold;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
