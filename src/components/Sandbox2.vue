<template lang="pug">
  .container
    h1 Sandbox2
    hr
    h2 スタイルの設定
    p(class="bg safe" :class="{large: isLarge, danger: hasError}") Hello, Joe!
    p(:class="[largeClass, dangerClass]") Hello, Joe!
    p(:class="classObject") Hello, Joe!
    hr
    h2 条件付きレンダリング
    v-btn(small @click="toggle") 切り替え
    p(v-if="show") Yes
    p(v-show="show") Yes
</template>

<script>
export default {
  name: 'Sandbox2',
  data () {
    return {
      isLarge: true,
      hasError: true,
      largeClass: 'large',
      dangerClass: 'danger',
      classObject: {
        large: true,
        'danger': true
      },
      show: true
    }
  },
  methods: {
    toggle: function() {
      this.show = !this.show
    }
  }
};
</script>

<style scoped>
.container {
  margin: 24px;
}
.large {
  font-size: 36px;
}
.danger {
  color: red;
}
.bg {
  background-color: grey;
}
/* 後ろのスタイルで上書き */
.safe {
  color: blue;
}
</style>
