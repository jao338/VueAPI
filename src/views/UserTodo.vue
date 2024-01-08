<template>
  <div class="userTODO mt-3">
    
    <div class="d-flex justify-content-between align-items-center mb-4">
      <div>
        <h1>{{ user.name }}</h1>
        <h6>{{ user.email }}</h6>
      </div>

      <routerLink :to="{ name: 'home' }">
        <button class="btn btn-primary">Voltar</button>
      </routerLink>

    </div>

    <h4 class="mb-3">Lista de tarefas</h4>
    <div class="card mb-3" v-for="todo in user.todos" :key="todo.id">
      <div class="card-header">{{ todo.title }}</div>
      <div class="d-flex justify-content-between card-body">

        <div>{{ todo.description }}</div>
        <div>

          <svg v-if="todo.is_done" xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-check-square" viewBox="0 0 16 16">
            <path d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z"/>
            <path d="M10.97 4.97a.75.75 0 0 1 1.071 1.05l-3.992 4.99a.75.75 0 0 1-1.08.02L4.324 8.384a.75.75 0 1 1 1.06-1.06l2.094 2.093 3.473-4.425z"/>
          </svg>

          <svg v-else xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-square" viewBox="0 0 16 16">
            <path d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z"/>
          </svg>

        </div>

      </div>
    </div>
    
  </div>
</template>

<script>

export default {

  data(){
    return {
      user: {

      }
    }
  },

  mounted(){

    const userID = this.$route.params.id;

    fetch(`http://127.0.0.1:8000/api/users/${userID}`)
      .then(response => response.json())
      .then(res => this.user = res.data)

      document.title = "To do List"
  }

}

</script>
