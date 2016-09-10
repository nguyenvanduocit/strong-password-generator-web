<template>
  <div class="password-field">
    <a class="password" v-text="password" @click.prevent="copy"></a>
  </div>
</template>
<script>
  import generatePassword from 'password-generator'
  import clipboard from 'clipboard-js'
  export default{
    props: {
      length: {
        default: 6
      },
      memorable: {
        default: true
      },
      pattern: {
        default: null
      },
      prefix: {
        default: null
      }
    },
    data () {
      return {
        password: ''
      }
    },
    methods: {
      copy () {
        clipboard.copy(this.password)
      },
      generatePassword () {
        this.password = generatePassword(this.length, this.memorable, this.pattern, this.prefix)
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
<style lang="scss" scoped>
  a {
    display: block;
    width: 100%;
    max-width: 400px;
    margin: 0 auto;
    background: #323841;
    font-family: 'Roboto Mono', monospace;
    font-size: 30px;
    color: #FFFFFF;
    letter-spacing: 1.66px;
    padding: 20px 30px;
    text-align: center;
    text-decoration: none;
    cursor: copy;
    transition: all .5s ease-in-out;
    &:hover {
      box-shadow: 0px 0px 37px 7px rgba(49, 56, 64, 0.56);
      transform: scale(1.1);
    }
  }
</style>
