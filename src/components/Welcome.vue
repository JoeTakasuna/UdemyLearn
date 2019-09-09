<template lang="pug">
  .welcome
    p {{ message }}
    router-link.link(to="/top")
      v-btn top
    router-link.link(to="/todo-list")
      v-btn todo list
</template>

<script>
export default {
  name: 'welcome',
  data () {
    return {
      message: 'Hello, Joe!'
    }
  }
};
</script>

<style scoped>
.welcome {
  display: flex;
  flex-direction: column;
  text-align: center;
  margin: 24px;
}
.link {
  margin: 12px;
  text-decoration: none;
}
</style>
