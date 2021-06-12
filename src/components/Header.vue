<template>
  <header>
    <nav>
      <router-link to="/" class="brand">
        <img src="@/assets/ranek.svg" alt="Ranek">
      </router-link>
      <router-link to="/usuario" class="btn" v-if="$store.state.login">
        {{ usuario }}
      </router-link>
      <router-link to="/login" class="btn" v-else>
        Vender / Login
      </router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  computed: {
    usuario() {
      return this.$store.state.usuario.nome.replace(/ .*/, "");
    }
  }
}
</script>

<style scoped>
nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px 20px;
  box-shadow: 0 2px 4px rgba(30, 60, 90, 0.1);
}

.brand {
  padding: 10px 0;
}
.brand img {
  width: 90px;
}
</style>