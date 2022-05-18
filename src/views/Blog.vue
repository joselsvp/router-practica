<template>
  <Titulo texto="Este es el título de mi blog" />
  <div v-for="post in arrayBlog" :key="post.id">
      <router-link :to="`/blog/${post.id}`">{{post.title}}</router-link>
  </div>
</template>

<script>
import Titulo from "../components/Titulo.vue";
export default {
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
        const data = await fetch("https://jsonplaceholder.typicode.com/posts");
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

<style>
</style>