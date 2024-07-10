<script lang="ts">
import type ITarefa from '@/interfaces/ITarefa';
import { defineComponent, type PropType } from 'vue';

export default defineComponent({
    name: 'tarefaApp',
    data() {
        return {
            ativo: false
        }
    },
    props: {
        tarefa: {type: Object as PropType<ITarefa>, required: true}
    },
    methods: {
        finalizarTarefa() {
            this.ativo = !this.ativo;
        }
    }
})
</script>

<template>
    <div :class="[ativo ? 'finalizada' : '' ]" class="tarefa">
        <p>{{ tarefa.nome }}</p>
        <i @click="finalizarTarefa" class="fa-solid fa-square-check"></i>
    </div>
</template>

<style scoped>
.tarefa {
    display: flex;
    justify-content: space-between;
    align-items: center;

    border-radius: 10px;
    background-color: rgb(204, 79, 79);
    box-shadow: 4px 4px 4px rgba(0, 0, 0, .4);
    
    width: 550px;
    height: 80px;
    padding: 10px;
    margin: 20px auto;
}

.finalizada {
    background-color: rgb(79, 204, 79);
    box-shadow: 4px 4px 4px rgba(0, 0, 0, .4);
}

.finalizada p {
    text-decoration: line-through;
}

.tarefa p {
    font-size: 1.1rem;
}

.tarefa i {
    font-size: 1.5rem
}
</style>