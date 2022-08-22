<template>
    <box>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao  || 'Tarefa sem Descrição'}}
            </div>
            <div class="column">    
                <cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </box>
</template>
<script lang="ts">
import ITarefa from '@/interfaces/ITarefa'
import { defineComponent, PropType } from 'vue'
import Box from './Box.vue'
import Cronometro from './Cronometro.vue'

export default defineComponent({
    name: 'Tarefa',
    props:{
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    },
    components:{
        Cronometro,
   
        Box }
})
</script>
<style scoped>
    .box {
        background: #FAF0CA;
    }
</style>