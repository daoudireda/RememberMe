<template>
  <ul>
    <learning-ressources
      v-for="res in ressources"
      :key="res.id"
      :id="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    ></learning-ressources>
  </ul>
</template>

<script>
import LearningRessource from './LearningRessource.vue';
export default {
  components: {
    'learning-ressources': LearningRessource,
  },
  inject: ['ressources'],
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
