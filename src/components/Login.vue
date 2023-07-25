<template>
<div>
    <h1>Login Page Component</h1>
</div>

<div class="boxy">
    <input v-model="login_data.email" type="text" name="" id="email" placeholder="Email">
    <br>
    <input v-model="login_data.password" type="password" name="" id="password" placeholder="Password">
    <br>
    <button @click="submit_login" type="submit">Login</button>
</div>
    

  </template>
  
  <script>
  
  export default {
  name:"Login",
  data(){
    return {
        login_data:{
            email: "",
            password:"",
        }
    }
  },
  
  mounted(){ 
    
  },
  
  methods:{
    submit_login(){
        console.log("email: " + this.login_data.email);
        console.log("password: " + this.login_data.password);
    }
  }
  
  }
  </script>
  
  <style>
.boxy{
    border-width: 10px;
    border-color: blue;
    border-style: solid;
}
  </style>