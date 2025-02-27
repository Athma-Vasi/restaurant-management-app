<template>
  <Header />
  <h1>Hello {{ name }}, Welcome to Update Restaurant Page</h1>

  <form action="">
    <fieldset class="form">
      <legend>Update Restaurant</legend>

      <label for="update-name"></label>
      <input type="text" name="update-name" id="update-name" placeholder="Name" v-model="restaurant.name" />

      <label for="update-location"></label>
      <input type="text" name="update-location" id="update-location" placeholder="Location"
        v-model="restaurant.location" />

      <label for="update-phone"></label>
      <input type="text" name="update-phone" id="update-phone" placeholder="Phone" v-model="restaurant.phone" />

      <label for="update-website"></label>
      <input type="text" name="update-website" id="update-website" placeholder="Website" v-model="restaurant.website" />

      <button type="button" v-on:click="updateRestaurant">Update Restaurant</button>
    </fieldset>
  </form>

</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Update",

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

  methods: {
    async updateRestaurant() {
      try {
        console.group("Update Restaurant");
        console.log("Name: ", this.restaurant.name);
        console.log("Location: ", this.restaurant.location);
        console.log("Phone: ", this.restaurant.phone);
        console.log("Website: ", this.restaurant.website);
        console.groupEnd();

        let result = await axios.put(`http://localhost:3000/restaurants/${this.$route.params.id}`, this.restaurant);
        console.log(result);
        this.$router.push({ name: "Home" });
      } catch (error) {
        console.error(error);

      }
    }
  },

  async mounted() {
    try {
      let user = localStorage.getItem("user");
      this.name = JSON.parse(user).name;
      if (!user) {
        this.$router.push({ name: "SignUp" });
      }


      let restaurantId = this.$route.params.id;
      let { data } = await axios.get(`http://localhost:3000/restaurants/${restaurantId}`);
      console.log({ data });
      this.restaurant.location = data.location;
      this.restaurant.name = data.name;
      this.restaurant.phone = data.phone;
      this.restaurant.website = data.website;
    } catch (error) {
      console.error(error);
    }
  },


};
</script>
