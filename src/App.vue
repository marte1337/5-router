<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link :to="{ name: 'about' }">About</router-link>
    <!-- Dynamischer Link über Data Binding, greift auf "name"-Prop in index.js zu;
    der Link kann dort ggf global verändert werden und trotzdem bleibt alles heile -->
    <router-link :to="{ name: 'jobs' }">Jobs</router-link>
  </nav>
  
  <div>
    <button @click="redirect">Redirect</button>
    <button @click="forward">Go forward</button>
    <button @click="backward">Go backward</button>
  </div>

  <router-view/>
</template>


<script>
export default {
  methods: {
    // $router = etwas mit der momentane route machen (VS $route = information über die momentane route)
    //hier .go(+1) = einen Schritt in der History nach vorne springen; (1) geht auch
    forward() {
      this.$router.go(+1)
    },
    backward() {
      this.$router.go(-1)
    },

    redirect() {
      this.$router.push({ name: 'home' })
    }
  }
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
  text-decoration: none;
  padding: 10px;
  border-radius: 4px;
}

nav a.router-link-exact-active {
  color: white;
  background: crimson;
}
</style>
