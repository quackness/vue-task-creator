<template>
  <header>
    <h1>{{ title }}</h1>
    <Button v-show="homePage"
      @btn-click="$emit('toggle-add-task')"
      :text="btnTextVariation ? 'Close' : 'Add Task'"
      :color="btnTextVariation ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: String,
    btnTextVariation: Boolean,
  },
  components: {
    Button,
  },
  computed: {
    homePage() {
      if (this.$route.path === "/") {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px;
}
</style>
