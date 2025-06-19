<template>
  <div>
    login aqui
    <b-button homevariant="success" @click="logar()">logar</b-button>
    

  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'LoginView',
  components: {

  },
  methods: {

    logar() {
      // altera a variavel global para verificar se esta ou nao logado
      this.$store.state.logado = true


      if (this.$route.path !== '/home') {
        this.$router.push('/home')
      }


    }
  },
}
</script>

<style></style>