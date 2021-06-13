<template>
  <section>
    <div v-if="vendas">
      <h2>Vendas</h2>
      <article class="produtos-wrapper" v-for="(venda, index) in vendas" :key="index">
        <ProdutoItem v-if="venda.produto" :produto="venda.produto">
          <p class="vendedor">
            <span>Comprador: </span>
            <strong>{{ venda.comprador_id }}</strong>
          </p>
        </ProdutoItem>
        <div class="entrega">
          <h3>Entrega</h3>
          <ul v-if="venda.endereco">
            <li v-for="(item, index) in venda.endereco" :key="index">
              {{ index}}: {{ item }}
            </li>
          </ul>
        </div>
      </article>
    </div>
  </section>
</template>

<script>
import ProdutoItem from "@/components/ProdutoItem"
import { api } from "@/services"
import { mapState } from "vuex"
export default {
  name: "UsuarioVendas",
  components: { ProdutoItem },
  data() {
    return {
      vendas: null,
    }
  },
  computed: {
    ...mapState(["usuario", "login"])
  },
  methods: {
    getVendas() {
      api.get(`/transacao?vendedor_id=${this.usuario.id}`)
      .then(response => {
        this.vendas = response.data
      })
    }
  },
  watch: {
    login() {
      this.getVendas()
    }
  },
  created() {
    if(this.login) { 
      this.getVendas() 
    }
  }
}
</script>

<style scoped>
.produto-wrapper {
  margin-bottom: 40px;
}

.vendedor span {
  color: #e80;
}
.entrega {
  display: grid;
  grid-template-columns: minmax(100px, 200px) 1fr;
  grid-gap: 20px;
  margin-bottom: 60px;
}
h2 {
  margin-bottom: 20px;
}
h3 {
  justify-self: end;
  margin: 0;
}
</style>