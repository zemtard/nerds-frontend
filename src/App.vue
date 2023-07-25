<script setup>
import { RouterLink, RouterView } from 'vue-router'


</script>

<template>
  <header>
    {{ hasToken }}
    <br>
    <i>Please refresh after login and logout (got stuck trying to make it work smoothly)</i>
    <div>
      <div v-if="hasToken">
        <p>Welcome, authenticated user!</p>
        <nav>
          <RouterLink to="/home">Home</RouterLink>
          <RouterLink to="/reset-password">Change Password</RouterLink>
          <RouterLink @click="logout" to="/login">Logout</RouterLink>
        </nav>
      </div>
      <div v-else>
        <p>Please log in or register.</p>
        <nav>
          <RouterLink to="/login">Login</RouterLink>
          <RouterLink to="/register">Register</RouterLink>
        </nav>
      </div>
    </div>

  </header>

  <RouterView />
</template>

<script>


export default {
  name: "App",

  data() {
    return {
      hasToken: false,
    }
  },

  methods: {
    logout() {
      localStorage.removeItem("token");
      this.$router.push('/login');
    }
  },

  mounted() {
    //check if tokens there initially
    const token = localStorage.getItem('token');
    this.hasToken = !!token;
  },

  computed: {
    hasToken() {
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
  text-align: center;
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
