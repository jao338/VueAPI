<template>

  <div class="card" v-for="user in users" :key="user.id">
    <div class="card-body">
      <routerLink :to="{name: 'user-todo', params: {id:user.id}}">{{ user.name }}</routerLink>
    </div>
  </div>

</template>

<script>
// @ is an alias to /src


export default {
  name: 'HomeView',

  data() {
    return {
      users: [],
    }
  },

  mounted() {
    fetch('http://127.0.0.1:8000/api/users')
    .then(response => response.json())
    .then((res) => {
      this.users = res.data;
    });
  }
}
</script>
