<template>

<div>
    <h1>Home Page Component</h1>
    <p>Displaying status of server (secured endpoint): </p>
    {{ statusText }}
</div>
    
  </template>
  
  <script>
  import axios from 'axios';
  export default {
    name: "Home",
    
  data(){
    return {
        statusText: 'xd',
    }
  },
  
  mounted(){ 
    const token = localStorage.getItem('token');
    
axios.get('http://localhost:3000/status1', {headers: { //TRYING TO ACCESS A SECURED ENDPOINT
    'Authorization': 'Bearer ' + token //TODO I KEEP GETTING UNAUTHORIZED
}}).then((response) => {
    
    console.log("Response:", response.data);
    this.statusText = response.data;
  })
  .catch((error) => {
    
    console.error("Error occurred:", error.message);
  });
      
  },

  
  }
  </script>
  
  <style>

  </style>