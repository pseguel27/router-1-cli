<template>
  <Titulo texto="Ruta con parámetros" />
  <h2>Parámetros: {{ $route.params.id }}</h2>
  <h3>
    {{ this.articulo.id }} {{ this.articulo.title}}
  </h3>
  <p>
    {{ this.articulo.body}}
  </p>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
  data() {
    return {
      articulo: {}
    }
  },
  components: {
    Titulo
  },
  methods: {
    async consumirArticulo(){
      try {
        const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
        const objeto = await data.json()
        this.articulo = objeto
      } catch (error) {
        console.log(error)
      }
    }
  },
  created() {
    this.consumirArticulo()
  }
}
</script>

<style>

</style>