<template lang="pug">
  .container
    h1 BitcoinPrice
    section(v-if="hasError") Error.
    section(v-else)
      div(v-if="loading") Loading...
      div(v-else)
        ul
          li(v-for="(rate, currency) in bpi") {{ currency }} : {{ rate.rate_float | currencyDecimal }}
        br
        pre {{ bpi }}
</template>

<script>
import axios from 'axios'

export default {
  name: 'BitcoinPrice',
  data () {
    return {
      bpi: null,
      hasError: false,
      loading: true
    }
  },
  created: function() {
    axios.get('https://api.coindesk.com/v1/bpi/currentprice.json')
    .then(response => {
      this.bpi = response.data.bpi
    })
    .catch(error => {
      alert(error)
      this.hasError = true
    })
    .finally(function() {
      this.loading = false
    }.bind(this))
  },
  filters: {
    currencyDecimal(value) {
      return value.toFixed(2)
    }
  }
};
</script>

<style scoped>
.container {
  margin: 24px;
}
</style>
