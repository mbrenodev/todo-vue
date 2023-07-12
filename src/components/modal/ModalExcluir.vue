<template>
  <div>
    <v-dialog v-model="dialog" persistent max-width="290">
      <v-card>
        <v-card-title class="text-h5"> Excluir </v-card-title>
        <v-divider />
        <v-card-text>
          Tem certeza que deseja excluir ?
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn 
            color="green darken-1" 
            text 
            @click="$emit('closeModal')"
          >
            Cancelar
          </v-btn>
          <v-btn 
            color="red darken-1" 
            text 
            @click="handleExcluirTarefa"
          >
            Excluir
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
    };
  },
  methods: {
    handleExcluirTarefa(){
      this.$store.dispatch('removeTarefa', this.tarefa.id)
      this.$emit('closeModal')
    }
  }
};
</script>

<style>
</style>