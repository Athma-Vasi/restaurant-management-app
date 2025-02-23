<template>
  <header>
    <nav>
      <a href="#">Home</a>
      <a href="#">Add Restaurant</a>
      <a href="#">Update Restaurant</a>
      <a href="#">Logout</a>
    </nav>
  </header>
</template>

<script lang="js">
export default {
        name: "Header"
    }
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
