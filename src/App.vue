<template>
  <div id="app">
    <button v-on:click="alertButton">Click Me</button>
    <button v-on:click="counterButton">
      Click on {{ FirstCounter }} times
    </button>
    <button v-on:click="counterButton2">
      Counting down from {{ SecondCounter }}
    </button>
    <button v-on:click="toggle">{{ toggleString }}</button>
    <p v-on:keypress="diceRoll">{{ diceText }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      FirstCounter: 0,
      SecondCounter: 10,
      toggleString: 'OFF',
      diceText: 'Press a key to roll the dice',
      
    };
  },
  methods: {
    alertButton() {
      alert('You clicked the button!');
    },
    counterButton() {
      this.FirstCounter++;
    },
    counterButton2() {
      if(this.SecondCounter > 0) {
        this.SecondCounter--;
      }
    },
    toggle() {
      if(this.toggleString === 'OFF') {
        this.toggleString = 'ON';
      } else {
        this.toggleString = 'OFF';
      }
    },
    //Press a numkey between 1-9 to roll a dice between it and 0
    diceRoll(e) {
      e = e.KeyCode;
      if(e.key >= 49 && e.key <= 57) {
        this.diceText = 'You rolled a ' + e.key + '!';
      } else {
        this.diceText = 'Press a numkey between 1-9 to roll a dice between it and 0';
      }
    },
  },
};
</script>

<style>
div {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  border: 1px solid black;
  padding: 2rem;
  margin-left: auto;
  margin-right: auto;
  width: 40%;
}
</style>