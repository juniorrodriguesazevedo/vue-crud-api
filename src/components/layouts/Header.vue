<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-md">
      <nav class="nav">
        <router-link class="nav-link" :to="{ name: 'Home' }">
          Inicio
        </router-link>
        <router-link class="nav-link" :to="{ name: 'Create' }">
          Criar
        </router-link>
      </nav>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.nav-link {
  color: #ffffff;
}
</style>