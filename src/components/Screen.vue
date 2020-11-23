<template>
  <div class="urn-screen">
    <div v-if="screen != 'fim'" class="urn-screen-vote">
      <div class="urn-screen-vote-texts">
        <div class="urn-screen-vote-title">Seu voto para:</div>
        <div class="urn-screen-vote-type">{{ screen }}</div>
        <div class="urn-screen-vote-numbers">
          Números

          <div
            class="urn-screen-vote-number"
            v-for="(value, key) in voteNumber.padEnd(numberQuantity, ' ')"
            v-bind:key="key"
          >
            {{ value }}
          </div>
        </div>
      </div>
      <div class="urn-screen-vote-image"></div>
      <div class="urn-screen-vote-instructions"></div>
    </div>

    <div v-if="screen == 'fim'" class="urn-screen-end">Voto realizado</div>
  </div>
</template>

<script>
export default {
  name: "Screen",
  props: {
    screen: String,
    voteNumber: String,
    numberQuantity: Number,
  },
};
</script>

<style>
.urn-screen {
  width: 55%;
  height: 100%;
  background-color: var(--ballot-box-screen-color);
  border: 2px solid var(--light-border-color);
  padding: 20px;
  color: var(--dark-text-color);
  border-radius: 5px;
}

.urn-screen-vote-title {
  font-size: 20px;
}

.urn-screen-vote-type {
  font-size: 30px;
  font-weight: bold;
  margin: 20px 0;
  text-transform: uppercase;
}
</style>