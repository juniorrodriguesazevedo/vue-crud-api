<template>
  <form @submit.prevent="sendNewUser" class="container">
    <div class="mb-3">
      <label class="form-label">Nome</label>
      <input
        class="form-control"
        v-model="user.name"
        type="text"
        name="name"
        required
      />
    </div>
    <div class="mb-3">
      <label class="form-label">Email</label>
      <input
        class="form-control"
        v-model="user.email"
        type="email"
        name="email"
        required
      />
    </div>
    <div>
      <button class="btn btn-success" type="submit">Salvar</button>
      <button @click.prevent="clearForm()" class="btn btn-warning">
        Limpar
      </button>
    </div>
  </form>
</template>

<script>
import api from "../../api/api.js";

export default {
  name: "CreateForm",
  data() {
    return {
      user: {
        name: "",
        email: "",
      },
    };
  },

  methods: {
    sendNewUser() {
      api
        .post("users", {
          name: this.user.name,
          email: this.user.email,
        })
        .then((res) => {
          console.log(res.data);
          alert(res.data.message);
          window.location.href = "/";
        })
        .catch((error) => {
          const errors = error.response.data.errors;
          console.log(errors);
          for (const error in errors) {
            const element = errors[error];
            alert(element);
          }
        });
    },

    clearForm() {
      this.user = {};
    },
  },
};
</script>

<style scoped>
form {
  margin-top: 50px;
  width: 500px;
}
</style>