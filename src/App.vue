<template>
  <div>
    <Header></Header>
    <div class="content">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Header from "./components/layouts/Header.vue";

export default {
  name: "App",
  components: {
    Header,
  },
};
</script>

<style scoped>
.content {
  margin: 20px auto;
  text-align: center;
}
</style>
