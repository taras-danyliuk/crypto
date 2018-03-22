<template>
  <div class="block">
    <div class="row">
      <span class="title">MD5:</span>
      <span class="value">{{md5}}</span>
    </div>

    <div class="row">
      <span class="title">SHA1:</span>
      <span class="value">{{sha1}}</span>
    </div>

    <div class="row">
      <span class="title">SHA256:</span>
      <span class="value">{{sha256}}</span>
    </div>

    <div class="row">
      <span class="title">SHA512:</span>
      <span class="value">{{sha512}}</span>
    </div>

    <div class="row">
      <span class="title">SHA3/Keccak:</span>
      <span class="value">{{sha3}}</span>
    </div>

    <div class="row">
      <span class="title">RIPEMD-160:</span>
      <span class="value">{{ripemd160}}</span>
    </div>
  </div>
</template>

<script>
const CryptoJS = require('crypto-js')

export default {
  prop: {
    input: String
  },
  name: 'hash',
  props: ['input'],
  data () {
    return {
      msg: 'New message'
    }
  },
  computed: {
    md5 () { return CryptoJS.MD5(this.input).toString() },
    sha1 () { return CryptoJS.SHA1(this.input).toString() },
    sha256 () { return CryptoJS.SHA256(this.input).toString() },
    sha512 () { return CryptoJS.SHA512(this.input).toString() },
    sha3 () { return CryptoJS.SHA3(this.input).toString() },
    ripemd160 () { return CryptoJS.RIPEMD160(this.input).toString() }
  }
}
</script>

<style scoped>
  .block {
    width: 49%;
    display: flex;
    flex-direction: column
  }

  .row {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    padding: 5px 10px;
    border: 1px solid grey;
  }

  .title {
    width: 110px;
    /*border-right: 1px solid red;*/
    flex-shrink: 0;
    text-align: left;
  }

  .value {
    word-break: break-all;
  }
</style>
