<template>
  <div>
    <button v-on:click="clearContent">Clear Data</button>
    <pre>{{ content | pretty }}</pre>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "Display",
  components: {},
  props: {
    content: String
  },
  methods: {
    clearContent() {
      this.content = null;
    }
  }
};
</script>

<style scoped>
* {
  margin-top: 2%;
  text-align: left;
}
</style>