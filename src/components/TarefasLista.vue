<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronoMetro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </Box>
</template>
<script lang="ts">
import ITarefa from '../interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';
import CronoMetro from './CronoMetro.vue';
import Box from './BoxTemplate.vue';

export default defineComponent({
  name: 'TarefasLista',
  components: {
    CronoMetro,
    Box
  },
  props: {
    tarefa: {
        type: Object as PropType<ITarefa>,
        required: true
    }
    
  }  
})
</script>

