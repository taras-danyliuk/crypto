<template>
  <div class="block" v-if="secret">
    <div class="row">
      <span class="title">HMAC MD5:</span>
      <span class="value">{{md5}}</span>
    </div>

    <div class="row">
      <span class="title">HMAC SHA1:</span>
      <span class="value">{{sha1}}</span>
    </div>

    <div class="row">
      <span class="title">HMAC SHA256:</span>
      <span class="value">{{sha256}}</span>
    </div>

    <div class="row">
      <span class="title">HMAC SHA512:</span>
      <span class="value">{{sha512}}</span>
    </div>

    <div class="row">
      <span class="title">HMAC SHA3:</span>
      <span class="value">{{sha3}}</span>
    </div>

    <div class="row">
      <span class="title">HMAC RIPEMD-160:</span>
      <span class="value">{{ripemd160}}</span>
    </div>
  </div>
  <div class="block" v-else>
    <p>Yo need to specify `secret` for this!</p>
  </div>
</template>

<script>
const CryptoJS = require('crypto-js')

export default {
  name: 'hmac',
  props: ['input', 'secret'],
  computed: {
    md5 () { return CryptoJS.HmacMD5(this.input, this.secret).toString() },
    sha1 () { return CryptoJS.HmacSHA1(this.input, this.secret).toString() },
    sha256 () { return CryptoJS.HmacSHA256(this.input, this.secret).toString() },
    sha512 () { return CryptoJS.HmacSHA512(this.input, this.secret).toString() },
    sha3 () { return CryptoJS.HmacSHA3(this.input, this.secret).toString() },
    ripemd160 () { return CryptoJS.HmacRIPEMD160(this.input, this.secret).toString() }
  }
}
</script>

<style scoped>
  .block {
    width: 49%;
    display: flex;
    flex-direction: column;
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
