<template>
  <div class="urn-keyboard">
    <div class="urn-keyboard-numeric">
      <div class="urn-keyboard-numeric-row">
        <button>1</button>
        <button>2</button>
        <button>3</button>
      </div>

      <div class="urn-keyboard-numeric-row">
        <button>4</button>
        <button>5</button>
        <button>6</button>
      </div>

      <div class="urn-keyboard-numeric-row">
        <button>7</button>
        <button>8</button>
        <button>9</button>
      </div>

      <div class="urn-keyboard-numeric-row">
        <button>0</button>
      </div>
    </div>

    <div class="urn-keyboard-actions">
      <button class="btn-branco">BRANCO</button>
      <button class="btn-corrige">CORRIGE</button>
      <button class="btn-confirma">CONFIRMA</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Keyboard",
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