<template>
  <div class="container">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Nome</th>
          <th scope="col">Email</th>
          <th class="options" scope="col">Opções</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <th scope="row">{{ user.id }}</th>
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
          <td>
            <router-link
              class="btn btn-info"
              :to="{ name: 'Edit', params: { id: user.id } }"
            >
              Editar
            </router-link>
            <button @click="deleteUser(user.id)" class="btn btn-danger">
              Deletar
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import api from "../api/api.js";

export default {
  name: "Table",
  data() {
    return {
      users: {},
    };
  },

  methods: {
    getUsers() {
      api
        .get("users")
        .then((res) => {
          this.users = res.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    deleteUser(id) {
      api
        .delete("users/" + id)
        .then((res) => {
          console.log(res.data);
          alert(res.data.message);
          window.location.href = "/";
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },

  created() {
    this.getUsers();
  },
};
</script>

<style scoped>
.table {
  margin: 25px auto;
}

.options {
  width: 200px;
}
</style>