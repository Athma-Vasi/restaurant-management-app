<template>
  <Header />
  <h1>Hello {{ name }}, Welcome to Add Restaurant Page</h1>

  <form action="">
    <fieldset class="form">
      <legend>Add Restaurant</legend>

      <label for="add-name"></label>
      <input type="text" name="add-name" id="add-name" placeholder="Name" v-model="restaurant.name" />

      <label for="add-location"></label>
      <input type="text" name="add-location" id="add-location" placeholder="Location" v-model="restaurant.location" />

      <label for="add-phone"></label>
      <input type="text" name="add-phone" id="add-phone" placeholder="Phone" v-model="restaurant.phone" />

      <label for="add-website"></label>
      <input type="text" name="add-website" id="add-website" placeholder="Website" v-model="restaurant.website" />

      <button type="button" v-on:click="addRestaurant">Add Restaurant</button>
    </fieldset>
  </form>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Add",
  components: {
    Header,
  },

  data() {
    return {
      name: "",
      restaurant: {
        name: "",
        location: "",
        phone: "",
        website: "",
      }
    };
  },

  components: {
    Header,
  },

  methods: {
    async addRestaurant() {
      try {
        console.group("Add Restaurant");
        console.log("Name: ", this.restaurant.name);
        console.log("Location: ", this.restaurant.location);
        console.log("Phone: ", this.restaurant.phone);
        console.log("Website: ", this.restaurant.website);
        console.groupEnd();

        let uuid = crypto.randomUUID();
        let result = await axios.post("http://localhost:3000/restaurants", {
          id: uuid,
          name: this.restaurant.name,
          location: this.restaurant.location,
          phone: this.restaurant.phone,
          website: this.restaurant.website,
        });
        console.log("Result: ", result);

        if (result.status === 201) {
          alert("Restaurant added successfully");
          this.$router.push({ name: "Home" });
        } else {
          alert("Failed to add restaurant");
        }

      } catch (error) {
        console.error(error);

      }
    }
  },

  mounted() {
    let user = localStorage.getItem("user");
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>
