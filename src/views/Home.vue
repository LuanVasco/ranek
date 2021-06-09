<template>
  <section>
    <h1>👍 Compre ou Venda 🤙</h1>
    <ProdutosBuscar />
    <ProdutosLista />
  </section>
</template>

<script>
import ProdutosBuscar from "@/components/ProdutosBuscar"
import ProdutosLista from "@/components/ProdutosLista"
export default {
  name: "Home",
  components: {
    ProdutosBuscar,
    ProdutosLista,
  }
}
</script>

<style scoped>
h1 {
  font-size: 2rem;
  color: #87F;
  margin-top: 40px;
  text-align: center;
}
</style>