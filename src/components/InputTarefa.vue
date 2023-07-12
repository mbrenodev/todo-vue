<template>
  <v-col cols="12">
    <v-text-field
      v-model="campoInput"
      label="Insira sua tarefa"
      outlined
      clearable
      @keyup.enter="handleAddTarefa"
    ></v-text-field>
  </v-col>
</template>

<script>
import TarefaList from './tarefas/TarefaList.vue';
export default {
  name: "InputTarefa",
  data() {
    return {
      campoInput: null,
    };
  },
  components: {
    // eslint-disable-next-line vue/no-unused-components
    TarefaList
  },
  methods: {
    handleAddTarefa() {
      this.$store.dispatch("adicionaTarefa", this.campoInput);
      this.campoInput = null;
    },
  },
};
</script>

<style>
</style>