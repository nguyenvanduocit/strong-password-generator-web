<template>
  <div id="app">
    <p class="tip">Click to copy</p>
    <div class="panel">
      <a href="#" class="password" v-text="memorablePassword" @click.prevent="copy(memorablePassword)"></a>
      <a href="#" class="password" v-text="mediumPassword" @click.prevent="copy(mediumPassword)"></a>
      <a href="#" class="password" v-text="hardPassword" @click.prevent="copy(hardPassword)"></a>
    </div>
    <div class="footer"><a href="http://senviet.org" >SENVIET.ORG</a></div>
  </div>
</template>

<script>
  import 'normalize.css/normalize.css'
  import WebFront from 'webfontloader'
  import generatePassword from 'password-generator'
  import clipboard from 'clipboard-js'
  WebFront.load({
    google: {
      families: ['Roboto Mono']
    }
  })
  export default {
    components: {},
    data () {
      return {
        memorablePassword: '',
        mediumPassword: '',
        hardPassword: ''
      }
    },
    methods: {
      copy (password) {
        clipboard.copy(password)
      },
      generatePassword () {
        this.memorablePassword = generatePassword(6)
        this.mediumPassword = generatePassword(8, false)
        this.hardPassword = generatePassword(12, false, /[\w\d\?\-@*#]/)
      }
    },
    ready () {
      this.generatePassword()
      setInterval(() => {
        this.generatePassword()
      }, 500)
    }
  }
</script>

<style lang="scss">
  *{
    box-sizing: border-box;
  }
  body{
    background: #5F6E85;
    box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.10);
    text-align: center;
  }
  #app{
    display: flex;
    flex-direction: column;
    justify-content: center;
    min-height: 100vh;
    p.tip{
      font-family: 'Roboto Mono', monospace;
      font-size: 30px;
      text-transform: uppercase;
      color: #323841;
      margin-top: 0;
      margin-bottom: 20px;
    }
    .footer{
      margin-top: 30px;
      a{
        @extend p.tip;
        margin-bottom: 0;
      }
    }
    .panel{
      text-align: center;
      padding: 20px 50px;
      a.password{
        display: block;
        width: 100%;
        max-width: 500px;
        margin: 0 auto;
        background: #323841;
        font-family: 'Roboto Mono', monospace;
        font-size: 30px;
        color: #FFFFFF;
        letter-spacing: 1.66px;
        padding: 30px;
        text-align: center;
        text-decoration: none;
        cursor: copy;
        & + a.password{
          margin-top: 20px;
        }
        transition: all .5s ease-in-out;
        &:hover{
          box-shadow: 0px 0px 37px 7px rgba(49,56,64,0.56);
          transform: scale(1.1);
        }
      }
    }
  }
</style>
