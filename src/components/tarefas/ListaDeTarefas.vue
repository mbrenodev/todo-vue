<template>
  <div>
    <drop-list
      :items="tarefasComputadas"
      @reorder="$event.apply(tarefasComputadas)"
    >
      import TarefaList from "./TarefaList.vue"; import TarefaList from
      "./TarefaList.vue";
      <template v-slot:item="{ item, reorder }">
        <drag :key="item.id" :data="item">
          <TarefaList
            style="backgroung-color: white"
            :style="
              reorder
                ? { borderLeft: '2px solid #1976D2', marginLeft: '-2px' }
                : {}
            "
            :tarefa="item"
          />
          <v-divider />
        </drag>
      </template>
    </drop-list>
  </div>
</template>

<script>
import { Drag, Drop, DropList } from "vue-easy-dnd";
import TarefaList from "./TarefaList.vue";
export default {
  name: "ListaDeTarefas",
  components: {
    Drag,
    DropList,
    // eslint-disable-next-line vue/no-unused-components
    Drop,
    TarefaList,
  },
  computed: {
    tarefasComputadas() {
      return this.$store.state.tarefas;
    },
  },
};
</script>

<style>
</style>