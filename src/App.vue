<template>
  <div class="container-clock">
    <BaseWatch :styleSet="styleSet[1]" />
    <BaseWatch :styleSet="styleSet[2]" />
    <BaseWatch :styleSet="styleSet[0]" />
  </div>
</template>

<script>
import BaseWatch from "../src/components/BaseWatch.vue";

export default {
  data() {
    return {
      styleSet: [
        { background: "#0c0210" },
        { background: "#ffaa00" },
        { background: "#3e2900" }],
    };
  },
  name: "App",
  components: {
    BaseWatch
  }
};
</script>

<style scoped>
.container-clock {
  display: flex;
}
</style>
