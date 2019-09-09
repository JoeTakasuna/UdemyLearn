<template lang="pug">
  .container
    router-link.link(to="/")
      v-btn(x-small) welcome
    router-link.link(to="/todo-list")
      v-btn(x-small) todo
    router-link.link(to="/bitcoin-price")
      v-btn(x-small) bitcoin
    router-link.link(to="/sandbox")
      v-btn(x-small) sandbox
    router-link.link(to="/search-in-qiita")
      v-btn(x-small) qiita
    router-link.link(to="/sandbox2")
      v-btn(x-small) sandbox2
    router-link.link(to="/sandbox3")
      v-btn(x-small) sandbox3
    router-link.link(to="/sandbox4")
      v-btn(x-small) sandbox4
</template>

<script>
export default {
  name: 'HeaderMenu',
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
  justify-content: center;
}
.link {
  margin: 12px;
  text-decoration: none;
}
</style>
