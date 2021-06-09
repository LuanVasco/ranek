<template>
  <section class="produtos-container">
    <article v-for="produto in produtos" :key="produto.id">
      <img v-if="produto.fotos " :src="produto.fotos[0].src" :alt="produto.fotos[0].titulo">
      <p class="preco">{{ produto.preco }}</p>
      <h2 class="title">{{ produto.nome }}</h2>
      <p>{{ produto.descricao }}</p>
    </article>
  </section>
</template>

<script>
export default {
  data() {
    return {
      produtos: null,
    }
  },
  methods: {
    getProdutos() {
      fetch("http://localhost:3000/produto")
      .then(response => response.json())
      .then(response => {
        this.produtos = response;
      })
    }
  },
  created() {
    this.getProdutos();
  }
}
</script>

<style scoped>

</style>