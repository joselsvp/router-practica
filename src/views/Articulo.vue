<template>
  <Titulo texto="texto con parámetros" />
  <h2>Parámetro recibido: {{ $route.params.id }}</h2>
  <h2>ID {{articulo.id}} - {{articulo.title}}</h2>
  <p>{{articulo.body}}</p>
</template>

<script>
import Titulo from "../components/Titulo.vue";
export default {
  components: {
    Titulo,
  },
  data() {
    return {
      articulo: {},
    };
  },
  methods: {
    async consultarArticulo() {
      try {
        const data = await fetch(
          `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`
        );
        const objeto = await data.json();
        this.articulo = objeto
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.consultarArticulo();
  },
};
</script>

<style>
</style>