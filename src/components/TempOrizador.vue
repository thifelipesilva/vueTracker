<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronoMetro :tempoEmSegundos="tempoEmSegundos"/>
        <BotaoTemp 
          @clicado="iniciar" 
          icone="fas fa-play" 
          texto="play" 
          :desabilitado="cronometroRodando"
        />
        <BotaoTemp 
          @clicado="finalizar" 
          icone="fas fa-stop" 
          texto="stop" 
          :desabilitado="!cronometroRodando"
        />  
    </div> 
</template>   
<script lang="ts">
import { defineComponent } from 'vue';
import CronoMetro from './CronoMetro.vue';
import BotaoTemp from  './BotaoTemp.vue';

export default defineComponent({
    name: 'TempOrizador',
    emits: [
        'aoTemporizadorFinalizado'
    ],
    components: {
        CronoMetro,
        BotaoTemp
    },

    data(){
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    
    methods: {
        iniciar() {
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos++;
            }, 1000) //1 seg = 1000ms
        },
        finalizar() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }

    }
})
</script> 

