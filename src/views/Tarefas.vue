<template>
  <div>
    <v-col cols="12">
      <v-text-field
        v-model="campoInput"
        label="Qual sua tarefa?"
        outlined
        clearable
        @keyup.enter="handleAddTarefa"
      ></v-text-field>
    </v-col>
    <v-list flat subheader>
      <v-list-item-group multiple active-class="">
        <div v-for="(tarefa, index) in $store.state.tarefas" :key="index">
          <tarefa :tarefa="tarefa" />
        </div>
      </v-list-item-group>
    </v-list>
  </div>
</template>

<script>
/* eslint-disable */
import tarefa from "@/components/tarefas/tarefa.vue";

export default {
  name: "Tarefas",
  components: {
    tarefa,
  },
  data() {
    return {
      campoInput: null,
    };
  },
  methods: {
    handleAddTarefa() {
      this.$store.commit('adicionaTarefa', this.campoInput)
      this.$store.commit(this.campoInput = null)
    },
  },
};
</script>
