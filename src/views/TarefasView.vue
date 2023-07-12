<template>
  <div>
    <ListaDeTarefas />
    <div 
      v-if="!$store.state.tarefas.length"
      class="d-flex justify-center align-center animate__animated animate__zoomIn animate__delay-2s animate__slower-3s">
      <v-alert>
        <v-icon size="120" color="primary"> mdi-check </v-icon>
        <div>Nenhuma tarefa</div>
      </v-alert>
    </div>
  </div>
</template>

<script>
import ListaDeTarefas from "@/components/tarefas/ListaDeTarefas.vue";
export default {
  name: "TarefasView",
  components: {
    ListaDeTarefas,
  },
  created() {
    this.$store.commit("buscaTarefas");
  },
};
</script>
