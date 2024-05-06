<template>
  <div class="container">
    <h1>FST-7</h1>
    <h2>{{ selectedDay }}</h2>
    <v-select
      v-model="selectedDay"
      :items="dias"
      label="Selecione o dia da semana"
      @change="loadTreinos"
    >
    </v-select>
    <div v-if="treinos.length" class="treino-container">
      <div
        v-for="grupo in treinos"
        :key="grupo.grupamento_muscular"
        class="card"
      >
        <div class="treino-header">
          <h3>{{ grupo.grupamento_muscular }}</h3>
        </div>

        <div
          v-for="exercicio in grupo.exercicios"
          :key="exercicio.nome"
          class="treino-descricao"
        >
          <h4 class="treino-grupo-nome">
            {{ exercicio.nome }}
          </h4>
          <p class="treino-grupo-desc">
            {{ exercicio.series }} séries, {{ exercicio.repeticoes }} reps
          </p>
          <p class="treino-grupo-desc">
            {{ exercicio.descanso }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import mockData from "@/mock/mockData.js";

export default {
  data() {
    return {
      dias: ["Segunda-Feira", "Terça-Feira", "Quarta-Feira", "Quinta-Feira"],
      selectedDay: "Segunda-Feira",
      treinos: [],
    };
  },
  created() {
    this.loadTreinos();
  },
  methods: {
    loadTreinos() {
      this.treinos = mockData[this.selectedDay];
    },
  },
  watch: {
    selectedDay() {
      this.loadTreinos();
    },
  },
};
</script>

<style scoped>
p {
  line-height: 1.6rem;
}
.container {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 15px;
}
.treino-container {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}
.card {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 15px;
  border-radius: 5px;
  border: solid 1px #ccc;
  background: #181818;
}

.treino-header {
}

.treino-grupo-nome {
  text-transform: uppercase;
}

.treino-descricao {
}
</style>
