<template>
  <cronometro :tempoEmSegundos="tempoEmSegundos" />
  <button class="button" @click="iniciar" :disabled="cronometroRodando">
    <span class="icon">
      <i class="fas fa-play"></i>
    </span>
    <span>play</span>
  </button>

  <button class="button" @click="finalizar" :disabled="!cronometroRodando">
    <span class="icon">
      <i class="fas fa-stop"></i>
    </span>
    <span>stop</span>
  </button>
</template>
<script>
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "Temporizador",
  emits:[ 'capturarDados' ],
  components: { Cronometro },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false
    };
  },

  methods: {
    iniciar() {
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
    },

    finalizar() {
      this.cronometroRodando = false
      this.$emit('capturarDados', this.tempoEmSegundos)
      clearInterval(this.cronometro);
      this.tempoEmSegundos = 0;
    },
  },
});
</script>
