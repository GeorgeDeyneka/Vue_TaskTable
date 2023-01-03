<template>
  <h1 class="title">Task table</h1>
  <AgTableVue />
</template>

<script>
import AgTableVue from "./components/AgTable.vue";

export default {
  name: "App",
  components: {
    AgTableVue,
  },
};
</script>
<style>
body {
  display: flex;
  justify-content: center;
  align-items: center;
}

.title {
  margin-bottom: 20px;
}
</style>
