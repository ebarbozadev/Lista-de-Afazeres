<script lang="ts">
import Tarefa from './Tarefa.vue';
import type ITarefa from '@/interfaces/ITarefa';
import { defineComponent, type PropType } from 'vue';

export default defineComponent({
    name: 'tarefasApp',
    components: {
        Tarefa: Tarefa
    },
    props: {
        tarefas: { type: Array as PropType<ITarefa[]>, required: true }
    }
})
</script>

<template>
    <Tarefa class="tarefa" v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
</template>

<style scoped>
@media (max-width: 768px) {
    .tarefa {
        width: 90%;
    }
}
</style>