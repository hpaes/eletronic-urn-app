<template>
  <div class="urn-keyboard">
    <div class="urn-keyboard-numeric">
      <div class="urn-keyboard-numeric-row">
        <button v-on:click="addNumber(1)">1</button>
        <button v-on:click="addNumber(2)">2</button>
        <button v-on:click="addNumber(3)">3</button>
      </div>

      <div class="urn-keyboard-numeric-row">
        <button v-on:click="addNumber(4)">4</button>
        <button v-on:click="addNumber(5)">5</button>
        <button v-on:click="addNumber(6)">6</button>
      </div>

      <div class="urn-keyboard-numeric-row">
        <button v-on:click="addNumber(7)">7</button>
        <button v-on:click="addNumber(8)">8</button>
        <button v-on:click="addNumber(9)">9</button>
      </div>

      <div class="urn-keyboard-numeric-row">
        <button v-on:click="addNumber(0)">0</button>
      </div>
    </div>

    <div class="urn-keyboard-actions">
      <button class="btn-branco" v-on:click="blankVoting()">BRANCO</button>
      <button class="btn-corrige" v-on:click="correct()">CORRIGE</button>
      <button class="btn-confirma" v-on:click="confirm()">CONFIRMA</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Keyboard",
  props: {
    addNumber: Function,
    correct: Function,
    confirm: Function,
    blankVoting: Function,
  },
};
</script>

<style>
.urn-keyboard {
  width: 40%;
  height: 100%;
  background-color: var(--ballot-box-keyboard-color);
  border-radius: 5px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.urn-keyboard-numeric {
  width: 100%;
}

.urn-keyboard-numeric-row {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}
.urn-keyboard-numeric button {
  background-color: var(--ballot-box-keyboard-button-color);
  color: var(--light-text-color);
  font-size: 30px;
  border-radius: 5px;
  width: 80px;
  height: 50px;
}

.urn-keyboard-actions {
  width: 100%;
  display: flex;
  justify-content: space-around;
}

.urn-keyboard-actions button {
  color: var(--dark-text-color);
  font-size: 15px;
  border-radius: 5px;
  width: 30%;
  height: 50px;
}

.btn-branco {
  background: var(--ballot-box-white-button-color);
}

.btn-corrige {
  background: var(--ballot-box-correct-button-color);
}

.btn-confirma {
  background: var(--ballot-box-confirm-button-color);
}
</style>