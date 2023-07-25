<template>
    <div>
        <h1>Register Page Component</h1>
    </div>
    <div>
        <input v-model="register_data.email" type="text" name="" id="email" placeholder="Email">
    <br>
    <input v-model="register_data.full_name" type="" name="" id="name" placeholder="Full Name">
    <br>
    <input v-model="register_data.phone_number" type="text" name="" id="phone" placeholder="Phone Number">
    <br>
    <input v-model="register_data.password" type="password" name="" id="password" placeholder="Password">
    <br>
    <button @click="submit_register" type="submit">Register</button>
    </div>
    
      </template>
      
      <script>
      
      import axios from 'axios';

      export default {
      name:"Register",
      data(){
        return {
            register_data:{
            full_name: "",
            phone_number: "",
            email: "",
            password:"",
        }
        }
      },
      
      mounted(){ 
        
      },
      
      methods:{

    async submit_register() {
        console.log("email: " + this.register_data.email);
        console.log("password: " + this.register_data.password);
        console.log("name: " + this.register_data.full_name);
        console.log("phone: " + this.register_data.phone_number);
  
        try {
          const response = await axios.post('http://localhost:3000/user-register', this.register_data);
          console.log("Response:", response.data);
        } catch (error) {
          console.error('Error:', error.message);
        }
      },

  }
      
      }
      </script>
      
      <style>
    
      </style>