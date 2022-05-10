<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form">
                <input
                 type="text"
                 class="input" 
                 placeholder="Qual tarefa você deseja iniciar?"
                 v-model="descricao"
                />
            </div>
            <div class="column">
                <TempOrizador @aoTemporizadorFinalizado="finalizarTarefa"/>     
                
            </div>
        </div>
    </div>
</template>
<script lang="ts">

import { defineComponent } from 'vue';
import TempOrizador from './TempOrizador.vue';

export default defineComponent({
    name: 'Form-temp',
    emits: [
        'aoSalvaTarefa'
    ],
    components: {
        TempOrizador
    },
    data(){
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            this.$emit('aoSalvaTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao                
            })
            
            this.descricao = '';
        }
    }
})
</script>