<template>
  <v-app>
    <v-main>
      <VTrainingList />
    </v-main>

    <AppFooter />
  </v-app>
</template>

<script>
import VTrainingList from "./components/VTrainingList.vue";

export default {
  components: {
    VTrainingList,
  },
};
//
</script>

<style scoped></style>
