<template>
  <Header />
  <h1>Hello {{ name }}, Welcome to Add Restaurant Page</h1>
</template>

<script>
import Header from "./Header.vue";

export default {
  name: "Add",
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
