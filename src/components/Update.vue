<template>
  <Header />
  <h1>Hello {{ name }}, Welcome to Update Restaurant Page</h1>
</template>

<script>
import Header from "./Header.vue";

export default {
  name: "Update",
  data() {
    return {
      name: "",
    };
  },

  components: {
    Header,
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
