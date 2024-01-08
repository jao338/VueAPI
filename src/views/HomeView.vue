<template>

  <div class="mt-3">

    <h4 class="mb-3">Lista de usuários</h4>
    
    <div class="card mb-2" v-for="user in users" :key="user.id">
      <div class="card-body">
        <routerLink class="text-decoration-none" :to="{name: 'user-todo', params: {id:user.id}}">{{ user.name }}</routerLink>
      </div>
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
