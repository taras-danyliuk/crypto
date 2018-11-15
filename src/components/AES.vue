<template>
    <div>
      <p>AES 256</p>
      <input v-model="secret"/>

      <div class="row">
        <input class="input" v-model="data"/>
        <p>{{encryptedData}}</p>
      </div>

      <div class="row">
        <input class="input half-width" v-model="encData"/>
        <p class="half-width break-word">{{decryptedData}}</p>
      </div>
    </div>
</template>

<script>
const CryptoJS = require('crypto-js')

export default {
  name: 'aes',
  data () {
    return {
      data: 'yo',
      encData: 'U2FsdGVkX1/M+e5stMa+/f4Jdnb7K80gj4dnIdpSDiU=',
      secret: 'secret'
    }
  },
  computed: {
    encryptedData () {
      return CryptoJS.AES.encrypt(this.data, this.secret).toString()
    },
    decryptedData () {
      return CryptoJS.AES.decrypt(this.encData, this.secret).toString(CryptoJS.enc.Utf8)
    }
  }
}
</script>

<style scoped>
  .row {
    display: flex;
    justify-content: space-between;
    padding: 0 10px;
  }

  .input {
    width: 200px
  }

  .half-width {
    width: 50%;
  }

  .break-word {
    word-break: break-all;
  }
</style>
