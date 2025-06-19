<template>
  <div class="home">    
      home aqui

      <b-button homevariant="success" @click="logout()">logout</b-button>
  </div>  
</template>

<script>
// @ is an alias to /src


export default {
  name: 'HomeView',
  components: {
   
  },
  methods: {
    logout(){
      this.$store.state.logado = false
      if (this.$route.path !== '/') {
      this.$router.push('/')
    }

    }
  }
}
</script>
