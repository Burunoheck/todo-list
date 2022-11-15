<template>
  <v-container class="pa-12" fluid>
    <h1 class="h1">Lista com tarefas adicionáveis</h1>
    <v-form>
      <v-text-field @click:append-inner="adicionar" variant="solo" append-inner-icon="mdi-send" label="Nova Tarefa" v-model="novaTarefa" @keydown.enter="adicionar"></v-text-field>
    </v-form>
      <v-divider>
      </v-divider>
      <v-list>
        <v-list-item-group>
          <v-list-item class="ma-1" variant="outlined" v-for="tarefa of tarefas" :key="tarefa.titulo">
            <v-card>
            {{ tarefa.titulo }}
          </v-card>
          </v-list-item>
        </v-list-item-group>
      </v-list>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      novaTarefa: "",  
      tarefas: [
        {titulo: "tarefa 1"},
        {titulo: "tarefa 2"},
        {titulo: "tarefa 3"},
        ],
    };
  },
  methods: {
    adicionar(e) {
      e.preventDefault();
      this.tarefas.push({titulo: this.novaTarefa})
      this.novaTarefa = "";
    }
  }
};
</script>

<style>

</style>