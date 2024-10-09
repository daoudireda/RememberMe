<template>
  <the-header title="RememberMe"></the-header>
  <the-ressource></the-ressource>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheRessource from './components/learning-ressources/TheRessource.vue';
export default {
  components: {
    'the-header': TheHeader,
    'the-ressource': TheRessource,
  },
};
</script>



<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
