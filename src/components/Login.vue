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
</script>

<style scoped></style>
