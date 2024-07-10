<script lang="ts">
import {defineComponent} from 'vue';
import Header from './components/Header.vue';
import Tarefas from './components/Tarefas.vue';
import type ITarefa from './interfaces/ITarefa';

export default defineComponent({
  name: 'appPrincipal',
  data() {
    return {
      tarefasArr: [] as ITarefa[]
    }
  },
  components: {
    Header: Header,
    Tarefas: Tarefas
  },
  methods: {
    cadastrarTarefa(tarefa: ITarefa) {
      this.tarefasArr.push(tarefa);
    }
  }
})
</script>

<template>
  <Header @tarefa-adicionada="cadastrarTarefa" />
  <main>
    <Tarefas :tarefas="tarefasArr" />
  </main>
</template>

<style scoped>

</style>
