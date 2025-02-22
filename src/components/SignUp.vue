<template>
  <h2>Hi Athma!</h2>
  <img
    class="logo"
    src="../assets/restaurant-logo.png"
    alt="restaurant-logo"
    srcset=""
  />

  <div class="form">
    <label for="name"></label>
    <input type="text" placeholder="Name" id="name" v-model="name" />

    <label for="email"></label>
    <input type="email" placeholder="Email" id="email" v-model="email" />

    <label for="password"></label>
    <input
      type="password"
      placeholder="Password"
      id="password"
      v-model="password"
    />

    <label for="confirm-password"></label>
    <input
      type="password"
      placeholder="Confirm Password"
      id="confirm-password"
      v-model="confirmPassword"
    />

    <button type="submit" v-on:click="signUp">Register</button>
  </div>
</template>

<script lang="js">
import axios from 'axios';

export default {
    name: 'SignUp',
    data() {
        return {
            name: '',
            email: '',
            password: '',
            confirmPassword: ''
        }
    },

    methods: {
        async signUp() {
            try {
                console.group('User Registration');
                console.log('Name:', this.name);
                console.log('Email:', this.email);
                console.log('Password:', this.password)
                console.log('Confirm Password:', this.confirmPassword);
                console.groupEnd();

                let result = await axios.post("http://localhost:3000/users", {
                name: this.name,
                email: this.email,
                password: this.password
                })

                console.log(result);

                if(result.status === 201) {
                    // this.$router.push('/login');
                    alert('User registered successfully');
                }
            } catch (err) {
                console.log(err);
            }
        }
    }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form input {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.form button {
  padding: 0.5rem;
  border: none;
  border-radius: 5px;
  background-color: #f1356d;
  color: white;
  cursor: pointer;
}
</style>
