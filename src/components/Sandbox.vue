<template lang="pug">
  .container
    h1 Sandbox
    hr
    h2 テンプレート構文
    p(v-html="message2")
    v-btn(x-small @click="reserve") reserve!
    p(v-text="message2")
    p {{ price + 1 }}
    p {{ ok ? 'YES' : 'NO' }}
    p {{ price | priceFormat }}
    hr
    h2 算出プロパティ
    p {{ reversedMessage }}
    p base price:
      v-text-field(v-model="price")
    p tax included price:
      v-text-field(v-model="taxIncludedPrice")
    hr
    h2 監視プロパティ
    v-text-field(v-model="message")
</template>

<script>
export default {
  name: 'Sandbox',
  data () {
    return {
      message: 'Hello, Joe!',
      message2: 'Hello, <span style="color:red;">Joe!<span>',
      price: 30000,
      ok: true
    }
  },
  // props: {
  //   データの受け取り
  // },
  computed: {
    reversedMessage: function() {
      return this.message.split('').reverse().join('')
    },
    taxIncludedPrice: {
      get: function() {
        return parseInt(this.price * 1.08)
      },
      set: function(taxIncludedPrice) {
        this.price = Math.ceil(taxIncludedPrice / 1.08)
      }
    }
  },
  methods: {
    reserve: function() {
      this.message = this.message.split('').reverse().join('')
    }
  },
  // created: function() {
  //   インスタンスが作成された後に同期的に呼ばれるフック
  // },
  // mounted: function() {
  //   インスタンスがマウントされたちょうど後に呼ばれるフック
  // },
  filters: {
    priceFormat: value => {
      return value.toLocaleString()
    }
  },
  watch: {
    message: function(newValue, oldValue) {
      // eslint-disable-next-line
      console.log(newValue, oldValue)
    }
  }
};
</script>

<style scoped>
.container {
  margin: 24px;
}
p {
  margin: 12px;
}
</style>
