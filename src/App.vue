<template>
  <div id="app">
    <!-- se nao estiver logado, renderiza o loginView -->
    <div v-if="!$store.state.logado">
      <LoginView />
    </div>

    <!-- se estiver logado, renderiza a tela home -->
    <div v-if="$store.state.logado">
      <b-navbar toggleable="lg" type="dark" variant="info">
        <div>
          <b-button v-b-toggle.sidebar-1>Toggle Sidebar</b-button>
          <b-sidebar id="sidebar-1" title="Sidebar" shadow>
            <div style="display: flex; flex-direction: column; margin: 5%;">
              <!-- chamar uma rota -->
              <b-button homevariant="success" @click="got_to_router('/home')">Home</b-button>
              <b-button homevariant="success" @click="got_to_router('/about')">About</b-button>

            </div>
          </b-sidebar>
        </div>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item href="#">Link</b-nav-item>
            <b-nav-item href="#" disabled>Disabled</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
              <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
            </b-nav-form>

            <b-nav-item-dropdown text="Lang" right>
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown>

            <b-nav-item-dropdown right>
              <!-- Using 'button-content' slot -->
              <template #button-content>
                <em>User</em>
              </template>
              <b-dropdown-item href="#">Profile</b-dropdown-item>
              <b-dropdown-item href="#">Sign Out</b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>


      <div style="display: flex; ">
        <router-view />

      </div>

    </div>

  </div>
</template>

<script>
import LoginView from './views/login.vue';

export default {
  name: 'app',
  components: {
    LoginView
  },
  data: () => ({
    render: false
  }),

  methods: {
    got_to_router(router) {
      //  verifica se a rota passada é a que ja esta sendo renderizada
      if (router == '/home') {
        if (this.$route.path !== router) {
          this.$router.push(router)
        }
      }
      else if (router == '/about') {
        if (this.$route.path !== router) {
          this.$router.push(router)
        }
      }
    }
  },

  mounted() {
    this.$store.state.logado;
  },

}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
