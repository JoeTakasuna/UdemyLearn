<template lang="pug">
  .container
    h1 Sandbox3
    h2 イベントハンドリング
    p {{ counter }}
    v-btn(small @click="counter++") Click!
    v-btn(small @click="clickHandler($event, 'Vue.js')") Click!
    p {{ message }}
</template>

<script>
export default {
  name: 'Sandbox3',
  data () {
    return {
      counter: 0,
      message: ''
    }
  },
  methods: {
    clickHandler: function($event, message) {
      this.counter++
      this.message = message
    }
  }
};
</script>

<style scoped>
.container {
  margin: 24px;
}
</style>
