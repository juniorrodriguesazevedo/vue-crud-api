<template>
  <form @submit.prevent="updateUser(user.id)" class="container">
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
import api from "../../api/api";

export default {
  name: "EditForm",
  data() {
    return {
      user: {},
    };
  },

  methods: {
    getUser() {
      api
        .get("users/" + this.$route.params.id)
        .then((res) => {
          this.user = res.data;
          console.log(res);
        })
        .catch((error) => {
          console.error(error);
        });
    },

    updateUser(id) {
      api
        .put("users/" + id, {
          name: this.user.name,
          email: this.user.email,
        })
        .then((res) => {
          alert(res.data.message);
          window.location.href = "/";
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },

  created() {
    this.getUser();
  },
};
</script>

<style scoped>
form {
  margin-top: 50px;
  width: 500px;
}
</style>