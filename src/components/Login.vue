<template>
    <div>
      <h1>Login Page Component</h1>
    </div>
  
    <div class="box">
      <input v-model="login_data.username" type="text" name="" id="username" placeholder="Username">
      <br>
      <input v-model="login_data.password" type="password" name="" id="password" placeholder="Password">
      <br>
      <button @click="submit_login" type="submit">Login</button>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: "Login",
    data() {
      return {
        login_data: {
          username: "",
          password: "",
        },
      };
    },
  
    methods: {
      async submit_login() {
        console.log("email: " + this.login_data.username);
        console.log("password: " + this.login_data.password);
  
        try {
        const response = await axios.post('http://localhost:3000/user-login', this.login_data);
        console.log("Response:", response.data);

        const token = response.data.token;
        localStorage.setItem('token', token); //storing token in localstorage for later use

        this.$router.push("/home")
        

      } catch (error) {
        console.error('Error:', error.message);
      }
    },
    },
  };
  </script>
  
  <style>

  .box {
    border-width: 10px;
    border-color: rgb(48, 46, 46);
    border-style: solid;
    margin-left: 40%;
    display: inline-block;
    padding: 5px;
  }
  </style>
  