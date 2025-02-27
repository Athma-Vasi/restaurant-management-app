<template>
  <Header />
  <h1>Hello {{ name }}, Welcome to Home Page</h1>
  <table>
    <tr>
      <th>Restaurant Name</th>
      <th>Location</th>
      <th>Phone</th>
      <th>Website</th>
      <th>Update</th>
    </tr>
    <tr v-for="restaurant in restaurants" :key="restaurant.id">
      <td>{{ restaurant.name }}</td>
      <td>{{ restaurant.location }}</td>
      <td>{{ restaurant.phone }}</td>
      <td>{{ restaurant.website }}</td>
      <td><router-link :to="`/update/${restaurant.id}`">✏️</router-link></td>
    </tr>
  </table>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      name: "",
      restaurants: [],
    };
  },

  components: {
    Header,
  },

  async mounted() {
    let user = localStorage.getItem("user");
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }

    let result = await axios.get("http://localhost:3000/restaurants");
    console.log(result);
    this.restaurants = result.data
  },
};
</script>

<style scoped>
table {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td,
th {
  border: 1px solid #ddd;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: #ddd;
}
</style>