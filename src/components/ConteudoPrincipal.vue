<template>
    <main class="conteudo-principal">
        <section>
            <span class="subtitulo-lg cadastre">
                Cadastre o aluno:
            </span>
            <div class="componente-form-table">
      <form action="">
      <label for="btn-cadastrar" class="itens">Nome: </label>
      <input
        autocomplete="off" required
        type="text"
        id="btn-cadastrar"
        name="btn-cadastrar"
        v-model="nome"
        >
        <br><br>
      <label for="btn-cadastrar">Data de nascimento: </label>
      <input
        type="date"
        id="btn-cadastrar"
        name="btn-cadastrar"
        v-model="nascimento"
        >
        <br><br>
      <label for="btn-cadastrar">Instrumento que toca: </label>
      <input
        type="text"
        id="btn-cadastrar"
        name="btn-cadastrar"
        v-model="instrumento"
        >
        <br><br>
        <label for="btn-cadastrar">Professor: </label>
        <select
            name="btn-cadastrar"
            id="btn-cadastrar"
            v-model="professor"
            >
                <option value=""></option>
                <option value="0">Débora</option>
                <option value="1">Júlia</option>
                <option value="2">João</option>
                <option value="3">Paulo</option>
            </select>
        <br><br>
      <input
        class="botao"
        type="submit"
        value="Cadastrar"
        @click="exibir"
        >
      </form>
      </div>
        </section>
    </main>
</template>

<script>
export default {
  name: 'FuncionarioForm',
  props: {
    msg: String
  },
  data () {
    return {
      nome: '',
      nascimento: '',
      instrumento: '',
      professor: ''
    }
  },
  mounted() {
    console.log()
  },
  methods: {
    exibir() {
      console.log(this.nome, this.nascimento, this.instrumento, this.professor);
    }
  }
}
</script>

<style scoped>
.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #FFFAF3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}
.cadastre {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}
@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}
@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}
input, select {
  margin-left: .5rem;
  color: black;
  font-size: 15px;
  width: 100%;
  padding: 10px 5px 5px;
  border-radius: 5px;
  border-width: 3px;
}
.componente-form-table {
  width: 100%;
  display: flex;
  justify-content: space-evenly;
}
.itens{
    margin-bottom: 1rem;
}
.botao{
  margin-left: .5rem;
  color: #000000;
  font-size: 15px;
  width: 30%;
  padding: 5px 5px 5px;
  border-radius: 4px;
}
</style>