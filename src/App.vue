<template>
<div class="fondo">
  <!-- <Navbar/> -->
  <router-view/>
</div>

</template>

<script>
import Navbar from './components/Navbar.vue'

export default {
  components: {
    Navbar,
  }
}
</script>

<style scoped>
.fondo {
  background-image: url("./assets/fondo2.png");
  background-color: rgb(70, 37, 104);
  background-attachment: fixed;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* text-align: center; */
}

/* nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
