<template lang="pug">
  .container
    h1 {{ message }}
    router-link.link(to="/top")
      v-btn top
    router-link.link(to="/todo-list")
      v-btn todo list
    router-link.link(to="/bitcoin-price")
      v-btn bitcoin price
</template>

<script>
export default {
  name: 'Welcome',
  data () {
    return {
      message: 'Hello, Joe!'
    }
  }
};
</script>

<style scoped>
.container {
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
