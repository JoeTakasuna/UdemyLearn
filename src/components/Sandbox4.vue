<template lang="pug">
  .container
    h1 Sandbox4
    h2 フォーム入力バインディング
    h3 テキストフォーム
    v-text-field(v-model.lazy="message")
    p {{ message }}
    v-textarea(v-model="message2")
    pre {{ message2 }}
    pre {{ $data }}
    hr
    h3 選択フォーム
    v-checkbox(v-model="selected" label="A" value="A")
    v-checkbox(v-model="selected" label="B" value="B")
    v-checkbox(v-model="selected" label="C" value="C")
    v-radio-group(v-model="selected2" row)
      v-radio(label="A" value="A")
      v-radio(label="B" value="B")
      v-radio(label="C" value="C")
    v-select(:items="alphabets")
    v-select(:items="alphabets" multiple)
</template>

<script>
export default {
  name: 'Sandbox4',
  data () {
    return {
      message: '',
      message2: '',
      selected: ['A'],
      selected2: ['A'],
      alphabets: ['A', 'B', 'C']
    }
  }
};
</script>

<style scoped>
.container {
  margin: 24px;
}
</style>
