<template>
  <section>
    Pagina do Usuário: {{ usuario }}  
  </section>  
</template>

<script>
export default {
  name: "Usuario",
  computed: {
    usuario() {
      return this.$store.state.usuario
    }
  }
}
</script>

<style scoped>

</style>