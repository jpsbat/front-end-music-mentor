<template>
  <div class="">
    <h1>Exibindo Professores</h1>  
    <hr>

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
        <label for="btn-cadastrar">Faculdade que se formou: </label>
      <input
        type="text"
        id="btn-cadastrar"
        name="btn-cadastrar"
        v-model="faculdade"
        >
        <br><br>
      <input
        class="botao"
        type="submit"
        value="Cadastrar"
        @click="cadastrarNovoProfessor($event)"
        />
      </form>
    
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Nome</th>
          <th>Nascimento</th>
          <th>Faculdade</th>
          <th>Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="professor in professores"
          :key="professor.id"
        >
          <td>{{ professor.id }}</td>
          <td>{{ professor.nome_professor }}</td>
          <td>{{ professor.nascimento }}</td>
          <td>{{ professor.faculdade }}</td>
          <td>
              <button @click="atualizarProfessor(professor.id)">Alterar</button>
              <button @click="excluirProfessor(professor.id)">Excluir</button>
          </td>
         </tr>
        </tbody>
      </table>
      </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'ExibirProfessores',
  props: {
    msg: String,
  },
  data() {
    return {
      nome_professor: '',
      nascimento: '',
      faculdade: '',
      professores: [],
    }
  },
  mounted() {
    this.listar()
  },
  methods: {
    cadastrarNovoProfessor(e) {

    e.preventDefault();

    axios
      .post('http://localhost:3000/routes/professores/cadastrar', {
        "nome_professor": this.nome_professor,
        "nascimento": this.nascimento,
        "faculdade": this.faculdade
      })
      .then(response => {
        console.log(response);
        this.listar()
      })
      .catch(error => console.log(error))
    },
    listar() {
    axios
      .get('http://localhost:3000/routes/professores/listar')
      .then(response => {

        this.professores = response.data.data
      })
      .catch(error => console.log(error))
    },
    atualizarProfessor(id) {

      axios
          .get(`http://localhost:3000/routes/professores/${id}`)
          .then(response => {

            var nome = window.prompt("Nome do professor:", response.data.data.nome_professor);
            var nascimento_professor = window.prompt("Data de nascimento do professor:", response.data.data.nascimento);
            var faculdade_professor = window.prompt("Faculdade do professor:", response.data.data.faculdade);

            if (nome !== null) {

              axios
                  .patch(`http://localhost:3000/routes/professores/alterar/${id}`, {
                    nome_professor: nome,
                    nascimento: nascimento_professor,
                    faculdade: faculdade_professor,

                  })
                  .then(response => {
                      console.log(response);
                      this.listar();
                  })
                  .catch(error => console.log(error))

            } else {
              // Se o usuário clicou em "Cancelar" ou fechou a caixa de diálogo
              console.log("Você cancelou a operação.");
            }

          })
          .catch(error => console.log(error))

      },
      excluirProfessor(id) {

        // Exibe uma caixa de diálogo com uma pergunta
        var result = window.confirm("Você tem certeza que deseja excluir este professor?");

        // Verifica o resultado da ação do usuário
        if (result) {
          axios
            .delete(`http://localhost:3000/routes/professores/excluir/${id}`)
            .then(response => {
              console.log(response);
              this.listar()
            })
            .catch(error => console.log(error))
        } else {
          // Se o usuário clicar em "Cancelar" ou fechar a caixa de diálogo, executa o código aqui
          window.alert("O usuário cancelou a exclusão.");
        }
      }
    }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
hr {
  width: 40%;
  margin-bottom: 1rem;
}
input {
  margin-left: .5rem;
}
</style>