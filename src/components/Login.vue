<template>
  <img
    class="logo"
    src="../assets/restaurant-logo-ai.jpg"
    alt="restaurant-logo"
    srcset=""
  />

  <fieldset class="form">
    <legend>Login</legend>
    <label for="email"></label>
    <input type="email" placeholder="Email" id="email" v-model="email" />

    <label for="password"></label>
    <input
      type="password"
      placeholder="Password"
      id="password"
      v-model="password"
    />

    <button type="submit" v-on:click="login">Login</button>

    <p>
      Don't have an account? <router-link to="/register">Register</router-link>
    </p>
  </fieldset>
</template>

<script lang="js">
import axios from "axios";

export default {
    name: "Login",
    data() {
        return {
            email: "",
            password: "",
        };
    },

    mounted() {
        let user = localStorage.getItem("user");
        if (user) {
            this.$router.push({ name: "Home" });
        } else {
            this.$router.push({ name: "Login" });
        }
    },

    methods: {
        async login() {
            try {
                console.group("Login");
                console.log("Email: ", this.email);
                console.log("Password: ", this.password);
                console.groupEnd();

                let result = await axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`);
                console.log("Result: ", result);

                if (result.status===200 && result.data.length > 0) {
                    localStorage.setItem("user", JSON.stringify(result.data[0]));
                    this.$router.push({ name: "Home" });
                } else {
                    alert("Invalid email or password");
                }
            } catch (error) {
                console.error("Error: ", error);
            }
        }
    }
}
</script>

<style scoped></style>
