<template>

  <div id="app" class="container pt-5">
    <img alt="Vue logo" src="./assets/logo.png">

    <div class="card mb-3" v-for="user in users" :key="user.name">
      <div class="card-body">
        {{ user.name }}
      </div>
    </div>
  </div>
  
</template>

<script>


export default {
  name: 'App',
  components: {
    
  },

  data(){
    return {
      users: [],
    }
  },

  mounted(){
    fetch('http://127.0.0.1:8000/api/users')
      .then(response => response.json())
      .then((res) => {
          this.users = res.data
      });
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
