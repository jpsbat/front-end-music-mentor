<template>
  <BannerForm />
  <ConteudoAlunoVue />
  <ConteudoProfessorVue />
</template>

<script>
import BannerForm from './components/BannerForm';
import ConteudoAlunoVue from './components/ConteudoAluno.vue';
import ConteudoProfessorVue from './components/ConteudoProfessor.vue';

export default {

    name: 'App',
    components: {
      BannerForm,
      ConteudoAlunoVue,
      ConteudoProfessorVue
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
