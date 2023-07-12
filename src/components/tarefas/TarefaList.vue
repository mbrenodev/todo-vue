<template>
  <div>
    <v-list-item
      :class="{ 'light-blue lighten-4': tarefa.concluido }"
      @click="setStatusTarefa"
    >
      <template v-slot:default="{}">
        <v-list-item-action>
          <v-checkbox :input-value="tarefa.concluido"></v-checkbox>
        </v-list-item-action>

        <v-list-item-content>
          <v-list-item-title
            :class="{ 'text-decoration-line-through': tarefa.concluido }"
            >{{ tarefa.titulo }}</v-list-item-title
          >
        </v-list-item-content>
        <v-list-item-action>
          <TarefasMenu :tarefa="tarefa" />
        </v-list-item-action>

      </template>
    </v-list-item>
    <v-divider />
  </div>
</template>
<script>
import TarefasMenu from './TarefasMenu.vue';
export default {
  props: ["tarefa"],
  name: "TarefaList",
  components: {
    TarefasMenu
  },
  methods: {
    setStatusTarefa() {
      this.$store.dispatch('concluiTarefa', this.tarefa)
    },
    handleRemoveTarefa(id) {
      this.$store.dispatch('removeTarefa', id)
    }
  },
};
</script>
