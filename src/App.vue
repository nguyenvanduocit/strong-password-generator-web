<template>
  <div id="app">
    <p class="tip">Click to copy</p>
    <div class="panel">
      <password-field :length="6"></password-field>
      <password-field :length="12" :memorable="false"></password-field>
    </div>
    <div class="footer"><a href="http://senviet.org" >SENVIET.ORG</a></div>
  </div>
</template>

<script>
  import 'normalize.css/normalize.css'
  import PasswordField from './components/PasswordField.vue'
  import WebFront from 'webfontloader'
  WebFront.load({
    google: {
      families: ['Roboto Mono']
    }
  })
  export default {
    components: {
      PasswordField
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
      .password-field{
        & + .password-field{
          margin-top: 30px;
        }
      }
    }
  }
</style>
