<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa.">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <temporizador @capturarDados="finalizarTarefa"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent} from 'vue'
import Temporizador from './Temporizador.vue'


export default defineComponent({
  components: { Temporizador },
  name: 'Formulario',
  emits:['aoSalvar'],
  data(){
    return{
        descricao: ''
    }
  },
  methods: {
    finalizarTarefa(dado: number):void {
        this.$emit('aoSalvar', {
            duracaoEmSegundos: dado, 
            descricao: this.descricao
        })
        this.descricao = ''
    }
  }
})
</script>

<style>

</style>