<template>
  <div>
  用户名：<input v-model="username"/>
  密码：<input v-model="password"/>
  图形验证码：<input v-model="imageCode"/>
  <img src="http://47.94.147.215:8080/code/image"/>
  <button @click="login">登陆</button>
  </div>
</template>

<script>
import qs from 'qs'
export default {
  data () {
    return {
      username: '',
      password: '',
      imageCode: ''
    }
  },
  computed: {
  },
  created () {
  },
  methods: {
    login () {
      // this.$axios({
      //   method: 'post',
      //   url: 'http://47.94.147.215:8080/login',
      //   data: qs.stringify({
      //     username: this.username,
      //     password: this.password,
      //     imageCode: this.imageCode
      //   })
      // })
      this.$axios.post('http://47.94.147.215:8080/login',
        qs.stringify({
          username: this.username,
          password: this.password,
          imageCode: this.imageCode
        }))
        .then(res => {
          console.log(res)
        })
        .catch(err => {
          console.log(err)
        })
    }
    // login () {
    //   this.$axios.post('http://47.94.147.215:8080/login', {
    //     username: this.username,
    //     password: this.password,
    //     imageCode: this.vertificationCode
    //   })
    //     .then(res => {
    //       console.log(res)
    //     })
    //     .catch(err => {
    //       console.log(err)
    //     })
    // }
  }
}
</script>

<style>
</style>
