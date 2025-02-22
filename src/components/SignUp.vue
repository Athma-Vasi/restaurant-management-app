<template>
  <img
    class="logo"
    src="../assets/restaurant-logo-ai.jpg"
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

    <button type="submit" v-on:click="register">Register</button>
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
        async register() {
            try {
                if(this.password !== this.confirmPassword) {
                    alert('Passwords do not match');
                    return;
                }

                if(this.name.length === 0 || this.email.length === 0 || this.password.length === 0) {
                    alert('Please fill all the fields');
                    return;
                }

                let uuid = crypto.randomUUID();

                console.group('User Registration');
                console.log({ uuid });
                console.log('Name:', this.name);
                console.log('Email:', this.email);
                console.log('Password:', this.password)
                console.log('Confirm Password:', this.confirmPassword);
                console.groupEnd();


                let result = await axios.post("http://localhost:3000/users", {
                    id: uuid,
                    name: this.name,
                    email: this.email,
                    password: this.password
                })

                console.log(result);

                if(result.status === 201) {
                    localStorage.setItem('user', JSON.stringify(result.data));
                    this.$router.push({ name: 'Home' });
                }
            } catch (err) {
                console.log(err);
            }
        }
    }
}
</script>

<style scoped>
.logo {
  width: 300px;
  height: 300px;
  border-radius: 50%;
}

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
