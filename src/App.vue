<script setup>
import { RouterLink, RouterView} from 'vue-router'


</script>

<template>
    <header>
{{ hasTokenComp }}

<div>
    <!-- Elements shown when the token exists -->
    <div v-if="hasToken">
      <!-- Your content for authenticated users here -->
      <p>Welcome, authenticated user!</p>
      <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/reset-password">Change Password</RouterLink>
      <RouterLink @click="logout" to="/login">Logout</RouterLink>
      </nav>
      <!-- Other authenticated user elements -->
    </div>

    <!-- Elements shown when the token does not exist -->
    <div v-else>
      <!-- Your content for non-authenticated users here -->
      <p>Please log in or register.</p>
      <nav>
        <RouterLink to="/login">Login</RouterLink>
        <RouterLink to="/register">Register</RouterLink>
      </nav>
      <!-- Login and Register buttons or other non-authenticated user elements -->
    </div>
  </div>

</header>
<h1>Test app</h1>

<RouterView />

</template>

<script>


  export default {
    name: "App",
    
  data(){
    return {
      hasToken : false,
    }
  },

  methods:{
    logout(){
      localStorage.removeItem("token");
      this.$router.push('/login');
    }
  },
  
  mounted(){ 
    //check if tokens there initially
    const token = localStorage.getItem('token');
    this.hasToken = !!token;
  },
  
  computed: {
    hasTokenComp() {
      const token = localStorage.getItem('token');
      return !!token;
    },


}
  }

</script>


<style scoped>




header {
  line-height: 1.5;
  max-height: 100vh;
}

nav {
  width: 100%;
  font-size: 30px;
  text-align: right;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}


</style>
