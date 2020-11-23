<template>
  <div class="urn-screen">
    <div v-if="screen != 'end'" class="urn-screen-vote">
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

        <div class="urn-screen-vote-description">
          Nome:
          <strong>
            {{ candidato.nome ? candidato.nome : "___________" }}</strong
          >
        </div>

        <div class="urn-screen-vote-description">
          Partido:
          <strong>{{
            candidato.partido ? candidato.partido : "___________"
          }}</strong>
        </div>
      </div>
      <div v-if="candidato.imagem" class="urn-screen-vote-image">
        <img :src="candidato.imagem" />
      </div>
      <div class="urn-screen-vote-instructions">
        <p>Aperte a tecla:</p>
        <p>
          <span class="urn-screen-button-white">BRANCO</span> para VOTAR EM
          BRANCO
        </p>
        <p>
          <span class="urn-screen-button-orange">LARANJA</span> para CORRIGIR
        </p>
        <p><span class="urn-screen-button-green">VERDE</span> para confirmar</p>
      </div>
    </div>

    <div v-if="screen == 'end'" class="urn-screen-end">FIM</div>
  </div>
</template>

<script>
export default {
  name: "Screen",
  props: {
    screen: String,
    voteNumber: String,
    numberQuantity: Number,
    candidato: Object,
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

.urn-screen-vote {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
}

.urn-screen-vote-texts {
  flex: 1;
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

.urn-screen-vote-numbers {
  display: flex;
  align-items: center;
}

.urn-screen-vote-number {
  width: 45px;
  height: 55px;
  border: 1px solid var(--dark-border-color);
  margin-left: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
}

.urn-screen-vote-description {
  margin-top: 20px;
}

.urn-screen-vote-image img {
  width: 110px;
  height: 150px;
  border: 1px solid var(--dark-border-color);
}

.urn-screen-vote-instructions {
  border-top: 1px solid var(--dark-border-color);
  font-size: 13px;
  margin-top: 20px;
  padding-top: 10px;
  width: 100%;
}

.urn-screen-button-white {
  border: 1px solid;
  padding: 4px;
  border-radius: 5px;
}

.urn-screen-button-orange {
  background-color: var(--ballot-box-correct-button-color);
  padding: 4px;
  border-radius: 5px;
}

.urn-screen-button-green {
  background-color: var(--ballot-box-confirm-button-color);
  padding: 4px;
  border-radius: 5px;
}

.urn-screen-end {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 120px;
  width: 100%;
  height: 100%;
}
</style>