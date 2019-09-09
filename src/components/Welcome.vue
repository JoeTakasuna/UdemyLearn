<template lang="pug">
  .container
    h1 {{ message }}
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
