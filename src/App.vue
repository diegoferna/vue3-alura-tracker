<template>
  <main class="columns is-gapless is-multiline modo-escuro">
    <div class="column is-one-quarter">
        <barra-lateral/>
    </div>
    <div class="column is-three-quarter conteudo">
        <formulario @aoSalvar="salvarTarefas"/>
        <div class="lista" >
          <tarefa  v-for="(tarefa , index) in tarefas" :key="index" :tarefa="tarefa" />  
          
          <box class="outro"  v-if="verificaTarefa">
            Você não esta produtivo hoje =/
          </box>
        </div>
       
    </div>
  </main>
</template>
<script lang="ts">

import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import Tarefa from './components/Tarefa.vue'
import ITarefa from './interfaces/ITarefa'
import Box from './components/Box.vue'

export default {
  components: { BarraLateral, Formulario, Tarefa, Box},
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    verificaTarefa() : boolean {
        return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefas(tarefa: ITarefa): void{
      this.tarefas.push(tarefa)
    }
  }
  
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.lista {
  padding: 1.5rem;
}

.main {
  --bg-primario: #fff;
  --texto-primario: #000;
}
.main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo { 
  background-color: var(--bg-primario);
}

    .outro {
        background: #FAF0CA;
    }
</style>
