<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
    name: 'headerApp',
    emits: ['tarefaAdicionada'],
    data() {
        return {
            nome: '',
        }
    },
    methods: {
        registrarTarefa(evento: Event) {
            const target = evento.target as HTMLInputElement;
            this.nome = target.value;
        },
        cadastrarTarefa() {
            this.$emit('tarefaAdicionada', {nome: this.nome});
            this.nome = '';
        }
    }
})
</script>

<template>
    <header>
        <input @change="registrarTarefa" v-model="nome" type="text" id="inputTarefa" placeholder="Digite o nome da tarefa" />
        <button @click="cadastrarTarefa" :disabled="nome === ''">
            <i class="fa-solid fa-plus"></i>
        </button>
    </header>
</template>

<style scoped>
header {
    box-shadow: 4px 4px 4px rgba(0, 0, 0, .4);
    background-color: rgb(211, 211, 211);
    height: 60px;

    display: flex;
    align-items: center;
    justify-content: center;
}

input {
    height: 50px;
    width: 500px;

    padding-left: 10px;

    outline: none;
    border: none;
    border-bottom: 1px solid black;
    border-radius: 10px 0px 0px 10px;

    font-size: 1.4rem;
}

button {
    height: 50px;
    width: 50px;

    border: none;
    border-radius: 0px 10px 10px 0px;
    cursor: pointer;
}

@media (max-width: 768px) {
    input {
        width: 83%;
    }
}
</style>