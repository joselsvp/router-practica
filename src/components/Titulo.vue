<template>
  <h1>{{texto}}</h1>
</template>

<script>
export default {
    props: {
        texto: String
    }

}
</script>

<style scoped>
    h1 {
        color: blue;
    }
</style>