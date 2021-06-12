<template>
  <section class="produtos-container">
    <transition mode="out-in">
      <div v-if="produtos && produtos.length" class="produtos" key="produtos">
        <article v-for="(produto, index) in produtos" :key="index" class="produto">
          <router-link to="/"> 
            <img v-if="produto.fotos " :src="produto.fotos[0].src" :alt="produto.fotos[0].titulo">
            <p class="preco">{{ produto.preco }}</p>
            <h2 class="title">{{ produto.nome }}</h2>
            <p>{{ produto.descricao }}</p>
          </router-link>
        </article>
        <ProdutosPaginar 
          :produtosPorPagina="produtosPorPagina"
          :produtosTotal="produtosTotal"
        />
      </div>
      <div class="sem-resultados" v-else-if="produtos && produtos.length === 0" key="sem-resultado">
        <p>Busca sem resultados. Tente buscar outro termo</p>
      </div>
      <PaginaCarregando v-else key="carregando"/>
    </transition>
  </section>
</template>

<script>
import ProdutosPaginar from "@/components/ProdutosPaginar"
import { serialize } from "@/helpers"
import { api } from "@/services"
export default {
  components: {
    ProdutosPaginar
  },
  data() {
    return {
      produtos: null,
      produtosPorPagina: 6,
      produtosTotal: 0,
    }
  },
  methods: {
    getProdutos() {
      this.produtos = null
      setTimeout(() => {
        api.get(`/produto?_limit=${this.produtosPorPagina}${this.url}`)
        .then(response => {
          this.produtosTotal = Number(response.headers['x-total-count']);
          this.produtos = response.data;
        })
      }, 1500)
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
.produtos-container {
  max-width: 1000px;
  margin: 0 auto;
}
.produtos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 30px;
  margin: 30px
}
.produto {
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.1);
  padding: 10px;
  background: #FFF;
  border-radius: 4px;
  transition:  all 0.2s;
}
.produto:hover {
  box-shadow: 0 6px 12px rgba(30, 60, 90, 0.2);
  transform: scale(1.1);
  position:relative;
  z-index: 1;
}

.produto img {
  border-radius: 4px;
  margin-bottom: 20px;
}

.titulo {
  margin-bottom: 10px;
}

.preco {
  color: #e80;
  font-weight: 700;
}

.sem-resultados {
  text-align: center;
}
</style>