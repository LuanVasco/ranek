<template>
  <section>
    <h2 class="title">Crie a sua conta</h2>
    <transition mode="out-in">
      <button v-if="!criar" class="btn" @click="criar = true">Criar Conta</button>
      <UsuarioForm v-else>
        <button class="btn btn-user">Criar Usuário</button>
      </UsuarioForm>
    </transition>
  </section>  
</template>

<script>
import UsuarioForm from '@/components/UsuarioForm.vue'
export default {
  components: {
    UsuarioForm
  },
  name: "LoginCriar",
  data() {
    return {
      criar: false,
    }
  }
}
</script>

<style scoped>
.title {
  text-align: center;
  margin-top: 40px;
  margin-bottom: 10px;
}
.btn {
  width: 100%;
  max-width: 300px;
  margin-left: auto;
  margin-right: auto;
}


.btn-user {
  max-width: 100%;
}
</style>