<template>
  <div id="app" class="container-fluid mt-3">
    <div @click="logout" v-if="authenticated" class='d-none'>logout</div>
    <router-view @authenticated="setAuthenticated"/>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.form-control-plaintext {
  padding:0
}

</style>
<script>
export default {
  data() {
    return {
      class: {
        mainView: "ycol col-md-9 ml-sm-auto col-lg-10 px-4"
      },
      authenticated: false,
    };
  },
  created: function(){
    if(sessionStorage.getItem('token')==null){
      this.$router.replace({ name: 'login'})
    }
    if(sessionStorage.getItem('token')){
      this.authenticated = true;
      this.$router.replace({name: "home"})
    }  
  },
  mounted: function() {
  },
  methods: {
    setAuthenticated(status) {
      this.authenticated = status;
    },
    logout() {
      sessionStorage.removeItem('jwt-auth')
      sessionStorage.removeItem('token')
      this.authenticated = false;
      this.$router.replace({ name: "login" });
    }
  }
};
</script>
