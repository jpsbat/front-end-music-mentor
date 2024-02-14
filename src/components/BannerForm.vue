<template>
  <header class="banner">
    <div class="apresentacao">
      <p class="cabecalho-lg frase-cabecalho">
        <span class="texto-azul">Harmonize: Music Mentor
        </span>
      </p>
      <p class="corpo frase-cabecalho">
        <span class="texto-branco">Gerencie seus professores
          e alunos na palma da sua mão!
        </span>
      </p>

      <img src="../assets/images/foto-banner.png" alt="Banda tocando"
      class="foto-banner">

      <p class="subtitulo-lg">
        A plataforma definitiva para diretores de escolas
        de música que buscam simplificar e aprimorar o
        gerenciamento de professores e alunos.
      </p>
    </div>
  </header>
</template>

<script>
export default {
  name: 'BannerForm',
  props: {
    msg: String
  }
}
</script>

<style scoped>
.banner {
  padding: 4rem 7.5rem;
  color: var(--creme);

  display: flex;
  justify-content: space-between;
  align-items: center;
  column-gap: 3.25rem;
}

.frase-cabecalho {
  margin-bottom: 2rem;
}

.texto-branco {
  color: white;
}
.texto-azul {
  color: #04a5c4;
}

.foto-banner {
  width: 30rem;
}

@media only screen and (max-width: 1300px) {
  .banner {
    padding: 4rem 3.75rem;
    flex-direction: column;
    align-items: center;
    gap: 1rem
  }
}

@media only screen and (max-width: 767px) {
  .banner {
    padding: 4rem 1.5rem;
  }

  .foto-banner {
    width: min(200%, 21.25rem);
  }
}
</style>