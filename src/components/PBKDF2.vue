<template>
    <div>
      <p>PBKDF2</p>
      <p>{{value}}</p>
    </div>
</template>

<script>
const CryptoJS = require('crypto-js')

function getFBKDF2 (input, cb) {
  setTimeout(function () {
    const salt = CryptoJS.lib.WordArray.random(128 / 8)

    console.time('pbkdf2')
    const key512Bits1000Iterations = CryptoJS.PBKDF2(input, salt, { keySize: 512 / 32, iterations: 10000 })
    console.timeEnd('pbkdf2')

    cb(key512Bits1000Iterations.toString())
  })
}

export default {
  name: 'pbkdf2',
  props: ['input'],
  data () {
    return {
      value: ''
    }
  },
  created () {
    if (this.input) this.fbkdf2(this.input)
  },
  methods: {
    fbkdf2 (input) {
      this.value = 'Processing...'
      getFBKDF2(input, value => { this.value = value })
    }
  },
  watch: {
    input () {
      this.fbkdf2(this.input)
    }
  }
}
</script>

<style scoped>

</style>
