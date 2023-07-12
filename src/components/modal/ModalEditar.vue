<template>
  <div>
    <v-dialog v-model="dialog" persistent max-width="290">
      <v-card>
        <v-card-title class="text-h5"> Editar </v-card-title>
        <v-divider />
        <v-col cols="12">
          <v-text-field 
          label="Titulo" 
          v-model="titulo" 
          outlined
        ></v-text-field>
        </v-col>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn 
            color="red darken-1" 
            text 
            @click="$emit('closeModal')"
          >
            Cancelar
          </v-btn>
          <v-btn 
            color="green darken-1" 
            text 
            @click="handleEditarTarefa"
          >
            Editar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  props: ['tarefa'],
  data() {
    return {
      dialog: true,
      titulo: null
    };
  },
  created() {
    this.titulo = this.tarefa.titulo
  },
  methods: {
    handleEditarTarefa(){
      let novaTarefa = {
        titulo: this.titulo,
        id: this.tarefa.id
      }
      this.$store.dispatch('editarTarefa', novaTarefa)
      this.$emit('closeModal')
    }
  }
};
</script>

<style>
</style>