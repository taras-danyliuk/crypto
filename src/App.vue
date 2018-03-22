<template>
  <div id="app">
    <input type="text" v-model="input"/>
    <input type="text" v-model="secret"/>

    <div class="output-wrapper">
      <Hash :input="input"/>
      <HMAC :input="input" :secret="secret"/>
    </div>

    <PBKDF2 :input="input"/>

    <AES />
  </div>
</template>

<script>
import Hash from './components/Hash'
import HMAC from './components/HMAC'
import PBKDF2 from './components/PBKDF2'
import AES from './components/AES'

export default {
  name: 'App',
  components: {
    Hash,
    HMAC,
    PBKDF2,
    AES
  },
  data () {
    return {
      input: 'yo',
      secret: ''
    }
  }
}
</script>

<style>
  body {
    margin: 0;
  }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
  .output-wrapper {
    display: flex;
    justify-content: space-between;
    padding: 0 10px;
  }
</style>
