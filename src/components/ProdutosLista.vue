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
import { serialize } from "@/helpers"
import { api } from "@/services"
export default {
  data() {
    return {
      produtos: null,
      produtoPorPagina: 9,
    }
  },
  methods: {
    getProdutos() {
      api.get(`/produto?_limit=${this.produtoPorPagina}${this.url}`)
      .then(response => {
        this.produtos = response.data;
      })
    }
  },
  computed: {
    url() {
      const query = serialize(this.$route.query)
      return query;
    }
  },
  watch: {
    url() {
      this.getProdutos()
    }
  },
  created() {
    this.getProdutos();
  }
}
</script>

<style scoped>

</style>