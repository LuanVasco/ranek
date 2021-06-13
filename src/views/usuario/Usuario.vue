<template>
  <section>
    <section class="usuario">
      <nav class="sidenav">
        <ul>
          <li>
            <router-link :to="{name: 'usuario'}">Produtos</router-link>
          </li>
          <li>
            <router-link :to="{name: 'compras'}">Compreas</router-link>
          </li>
          <li>
            <router-link :to="{name: 'vendas'}">Vendas</router-link>
          </li>
          <li>
            <router-link :to="{name: 'usuario-editar'}">Editar Usuário</router-link>
          </li>
          <li>
            <button @click.prevent="deslogar">Deslogar</button>
          </li>
        </ul>
      </nav>
      <transition mode="out-in">
        <router-view></router-view>
      </transition>
    </section>
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
  },
  methods: {
    deslogar() {
      this.$store.dispatch("deslogarUsuario")
      this.$router.push("/login")
    }
  }
}
</script>

<style scoped>
.usuario {
  display: grid;
  grid-template-columns: minmax(140px, 200px) 1fr;
  grid-gap: 30px;
  max-width: 900px;
  margin: 40px auto;
  padding: 20px;
}
.sidenav a,
.sidenav button {
  padding: 10px;
  display: block;
  background: #f4f7fc;
  margin-bottom: 10px;
  border-radius: 4px;
}

.sidenav a.router-link-exact-active,
.sidenav a:hover,
.sidenav button:hover {
  background: #87f;
  color: #FFF;
}

.sidenav button {
  border: none;
  width: 100%;
  font-size: 1rem;
  font-family: "Avenir", Arial, Helvetica, sans-serif;
  text-align: left;
  cursor: pointer;
}

@media screen and (max-width: 500px) {
  .usuario {
    grid-template-columns: 1fr;
    margin: 0 auto;
  }
}
</style>