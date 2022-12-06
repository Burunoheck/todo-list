<template>
  <v-container class="pa-12" fluid>
    <h1 class="h1">Lista com tarefas adicionáveis</h1>
    <v-form>
      <v-text-field
        @click:append-inner="adicionar"
        variant="solo"
        append-inner-icon="mdi-send"
        label="Nova Tarefa"
        v-model="novaTarefa"
        @keydown.enter="adicionar"
      ></v-text-field>
    </v-form>
    <v-divider> </v-divider>
    <v-list>
      <v-list-item-group>
        <v-list-item
          class="ma-1"
          variant="outlined"
          v-for="(tarefa, i) of tarefas"
          :key="i"
        >
          <v-card class="pl-3">
            {{ tarefa.titulo }}
            <v-btn @click="removeTarefas(tarefa)">
              <v-icon>mdi-trash-can</v-icon>
            </v-btn>
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
        { titulo: "matemática", id: 1},
        { titulo: "física", id: 2},
        { titulo: "biologia", id: 3},
      ],
    };
  },
  methods: {
    adicionar(e) {
      e.preventDefault();
      this.tarefas.push({ titulo: this.novaTarefa, id: this.tarefas.length + 1});
      this.novaTarefa = "";
    },
    removeTarefas({ id }) {
      const index = this.tarefas.findIndex((item) => item.id === id);
      if (index > -1) {
        delete this.tarefas[index]
      }
    },
  },
};
</script>

<style></style>
