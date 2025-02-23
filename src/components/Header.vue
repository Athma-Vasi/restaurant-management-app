<template>
  <header>
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/add">Add Restaurant</router-link>
      <router-link to="/update">Update Restaurant</router-link>
      <a v-on:click="logout" href="#">Logout</a>
    </nav>
  </header>
</template>

<script lang="js">
export default {
  name: "Header",
  methods: {
    logout() {
      localStorage.removeItem("user");
      this.$router.push({ name: "Login" });
    }
  }
};
</script>

<style scoped>
header {
  background-color: #333;
  color: white;
}

nav {
  display: flex;
  justify-content: space-around;
}

a {
  color: white;
  text-decoration: none;
  font-size: larger;
  padding: 10px;
}

a:hover {
  background-color: #757575;
}
</style>
