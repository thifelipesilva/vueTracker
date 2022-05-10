<template>
    <section >
        <strong class="display">{{ tempoDecorrido }}</strong>
    </section>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'CronoMetro',
    props: {
        tempoEmSegundos: {
            type: Number,
            default: 0
        }
    },
    computed: {
        tempoDecorrido (): string {
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8)
            //construtor date precisa de um tempo em milisegundos. substr(da posicao 11, retornar 8 caracteres).
        }
    },
})
</script>
<style>
.display {
    color: var(--texto-primario);
}
</style>