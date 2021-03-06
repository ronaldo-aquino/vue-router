<template>
  <Titulo text="Dinâmico!" />
  <h2>Parametro = {{ artigo.id }}</h2>
  <h3>{{ artigo.title }}</h3>
  <p>{{ artigo.body }}</p>
</template>

<script>
import Titulo from "../components/Titulo";
export default {
  name: "Artigo",
  components: {
    Titulo,
  },

  data() {
    return {
      artigo: {},
    };
  },

  methods: {
    async consumirArtigo() {
      try {
        const id = this.$route.params.id;
        const url = `https://jsonplaceholder.typicode.com/posts/${id}`;
        const data = await fetch(url);
        const objeto = await data.json();
        this.artigo = objeto;
      } catch (error) {
        console.log(error);
      }
    },
  },

  created() {
    this.consumirArtigo();
  },
};
</script>

<style scoped>
</style>