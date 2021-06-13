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

</style>