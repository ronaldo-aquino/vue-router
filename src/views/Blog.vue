<template>
  <h2>Blog</h2>
  <Titulo text="Título do meu blog" />
  <!-- <button @click="consumirApi">Consumir API</button> -->
  <div v-for="item in arrayBlog" :key="item.id">
    <router-link :to="`/blog/${item.id}`">
      {{ item.title }}
    </router-link>
  </div>
</template>

<script>
import Titulo from "../components/Titulo";

export default {
  name: "Blog",
  components: {
    Titulo,
  },

  data() {
    return {
      arrayBlog: [],
    };
  },

  methods: {
    async consumirApi() {
      try {
        const url = "https://jsonplaceholder.typicode.com/posts";
        const data = await fetch(url);
        const array = await data.json();
        this.arrayBlog = array;
      } catch (error) {
        console.log(error);
      }
    },
  },

  created() {
    this.consumirApi();
  },
};
</script>

<style scoped>
</style>


