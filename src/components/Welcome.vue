<template lang="pug">
  .container
    h1 {{ message }}
    router-link.link(to="/top")
      v-btn top
    router-link.link(to="/todo-list")
      v-btn todo-list
    router-link.link(to="/bitcoin-price")
      v-btn bitcoin-price
    router-link.link(to="/sandbox")
      v-btn sandbox
    router-link.link(to="/search-in-qiita")
      v-btn search-in-qiita
    router-link.link(to="/sandbox2")
      v-btn sandbox2
    router-link.link(to="/sandbox3")
      v-btn sandbox3
    router-link.link(to="/sandbox4")
      v-btn sandbox4
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
