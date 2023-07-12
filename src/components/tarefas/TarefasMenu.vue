<template>
  <div>
    <v-menu bottom origin="center center" transition="scale-transition">
      <template v-slot:activator="{ on, attrs }">
        <v-btn icon v-bind="attrs" v-on="on">
          <v-icon dark> mdi-dots-vertical </v-icon>
        </v-btn>
      </template>

      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" @click="handleClick(item)">
          <v-icon left>
            {{ item.icone }}
          </v-icon>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
    <ModalEditar 
      v-if="items[0].modal" 
      @closeModal="items[0].modal = false"
      :tarefa="tarefa"
    />
    <ModalExcluir v-if="items[1].modal" 
      @closeModal="items[1].modal = false"
      :tarefa="tarefa" />
  </div>
</template>

<script>
import ModalEditar from "../modal/ModalEditar.vue";
import ModalExcluir from "../modal/ModalExcluir.vue";
export default {
  props:['tarefa'],
  components: { ModalEditar, ModalExcluir },
  data: () => ({
    items: [
      { 
        icone: "mdi-pencil-circle",
        title: "Editar",
        modal: false,
      },
      {
        icone: "mdi-delete-circle",
        title: "Excluir",
        modal: false,
      },
    ],
  }),
  methods: {
    handleClick(item) {
    item.modal = true;
  },
  }
};
</script>

<style>
</style>