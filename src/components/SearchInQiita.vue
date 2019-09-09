<template lang="pug">
  .container
    h1 SearchInQiita
    v-text-field(v-model="keyword")
    p {{ message }}
    ul
      li(v-for="item in items")
        a(:href='item.url' target="_blank") {{ item.title }}
</template>

<script>
import axios from 'axios'
import _ from 'lodash'

export default {
  name: 'SearchInQiita',
  data () {
    return {
      items: null,
      keyword: '',
      message: ''
    }
  },
  // props: {
  //   データの受け取り
  // },
  // computed: {
  //   データの算出
  // },
  methods: {
    getAnswer: function() {
      if (this.keyword === '') {
        this.items = null
        this.message = ''
        return
      }
      this.message = 'Loading...'
      var vm = this
      var params = { page: 1, per_page: 20, query: this.keyword }
      axios.get('https://qiita.com/api/v2/items', { params })
        .then(response => {
          vm.items = response.data
        })
        .catch(error => {
          vm.message = 'Error!' + error
        })
        .finally(() => { // これ可能？
          vm.message = ''
        })
    }
  },
  created: function() {
    this.debouncedGetAnswer = _.debounce(this.getAnswer, 1000)
  },
  // mounted: function() {
  //   インスタンスがマウントされたちょうど後に呼ばれるフック
  // }
  watch: {
    keyword: function() {
      this.message = 'Waiting for you to stop typing...'
      this.debouncedGetAnswer()
    }
  }
};
</script>

<style scoped>
.container {
  margin: 24px;
}
</style>
