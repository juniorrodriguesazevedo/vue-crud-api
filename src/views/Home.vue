<template>
  <div>
    <h1>Página Inicial</h1>
    <Table></Table>
  </div>
</template>

<script>
import Table from "../components/Table.vue";

export default {
  name: "Home",
  data() {
    return {};
  },
  components: {
    Table,
  },
};
</script>

<style scoped>
</style>