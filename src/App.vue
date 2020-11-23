<template>
  <div id="app">
    <div class="urn">
      <Screen
        :screen="screen"
        :voteNumber="voteNumber"
        :numberQuantity="numberQuantity"
        :candidato="candidato"
      />
      <Keyboard
        :addNumber="addNumber"
        :correct="correct"
        :confirm="confirm"
        :blankVoting="blankVoting"
      />
    </div>
  </div>
</template>

<script>
// CSS
import "@/css/global.css";

// Components
import Keyboard from "@/components/Keyboard";
import Screen from "@/components/Screen";

// Audios
import confirmAudio from "@/assets/audios/confirm.wav";
import keyAudio from "@/assets/audios/key.wav";

export default {
  name: "App",
  components: {
    Keyboard,
    Screen,
  },
  methods: {
    addNumber(number) {
      // Play button sound
      this.playSound(keyAudio);

      // Verify limit of voted numbers
      if (this.voteNumber.length == this.numberQuantity) {
        return false;
      }

      // Add selected number
      this.voteNumber += "" + number;

      // Verify voted candidate
      this.verifyCandidate();
    },

    verifyCandidate() {
      // Incomplete vote
      if (this.voteNumber.length < this.numberQuantity) {
        return false;
      }

      // Verify existing candidate
      if (this.candidatos[this.screen][this.voteNumber]) {
        this.candidato = this.candidatos[this.screen][this.voteNumber];
        return true;
        // Blank vote
      } else if (this.voteNumber == "00") {
        return (this.candidato = {
          nome: "Voto nulo",
          partido: "Voto nulo",
          imagem: "",
        });
      }

      // Not existing candidate
      this.candidato = {
        nome: "Candidato não existe",
        partido: "Canditato não existe",
        imagem: "",
      };
    },

    correct() {
      this.clean();
    },
    clean() {
      this.candidato = {};
      this.voteNumber = "";
    },
    confirm() {
      // Incomplete vote
      if (this.voteNumber.length < this.numberQuantity) {
        return false;
      }

      return this.nextScreen();
    },
    nextScreen() {
      // Play confirm button sound
      this.playSound(confirmAudio);

      // Vereador
      if (this.screen == "prefeito") {
        this.screen = "vereador";
        this.numberQuantity = 5;
        return this.clean();
      }

      // End voting session
      this.screen = "end";

      // Current instance
      const instance = this;

      // Return to start
      setTimeout(() => {
        instance.screen = "prefeito";
        instance.numberQuantity = 2;
        return instance.clean();
      }, 3000);
    },
    blankVoting() {
      // Ending screen
      if (this.screen == "end") {
        return false;
      }

      this.clean();
      this.nextScreen();
    },
    playSound(soundFile) {
      if (soundFile) {
        const audio = new Audio(soundFile);
        audio.play();
      }
    },
  },
  data() {
    return {
      screen: "prefeito",
      voteNumber: "",
      numberQuantity: 2,
      candidato: {},
      candidatos: {
        prefeito: {
          "01": {
            nome: "Ash",
            partido: "Pokemon",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/ash.png",
          },
          "08": {
            nome: "Vegeta",
            partido: "Dragon Ball",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/vegeta.png",
          },
        },
        vereador: {
          "01234": {
            nome: "Pikachu",
            partido: "Pokemon",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/pikachu.png",
          },
          "08001": {
            nome: "Goku",
            partido: "Dragon Ball",
            imagem:
              "https://raw.githubusercontent.com/william-costa/wdev-urna-eletronica-resources/master/images/goku.png",
          },
        },
      },
    };
  },
};
</script>

<style>
#app {
  background-color: var(--background-color);
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.urn {
  width: 1000px;
  height: 500px;
  background-color: var(--ballot-box-background-color);
  padding: 30px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
}
</style>
