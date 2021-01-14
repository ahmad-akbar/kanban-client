<template>
  <div>
    <Navbar :dataIsLogin="isLogin" :btnLogout="logout"></Navbar>
    <br>
    <Login v-if="!isLogin" :changeIsLogin="changeIsLogin"></Login>
    <Home v-if="isLogin"></Home>
  </div>
</template>

<script>
import Navbar from "./components/navbar.vue";
import Login from "./views/login.vue";
import Home from "./views/home";

export default {
  data() {
    return {
      isLogin: false
    };
  },
  components: {
    Navbar,
    Login,
    Home,
  },
  methods: {
    changeIsLogin(value){
      this.isLogin = value
    },

    logout(){
      localStorage.clear()
      this.isLogin = false
    }
  },
  created(){
    if(localStorage.access_token){
      this.isLogin = true
    } else {
      this.isLogin = false
    }
  }
};
</script>

<style scoped>
</style>