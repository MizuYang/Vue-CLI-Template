<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div class="btn btn-primary">測試 Bootstrap 載入</div>
    <p>測試千分位：一共 {{ $thousandths(1000) }} 元</p>
  </div>
  <IsLoading v-model:active="isLoading"></IsLoading>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
//! import emitter from '@/utils/emitter.js'
export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },

  data () {
    return {
      isLoading: false
    }
  },

  mounted () {
    this.isLoading = true
    this.$http.get('https://randomuser.me/api/')
      .then(res => {
        console.log(res)
        this.isLoading = false
      })
      .catch(err => {
        console.log(err)
      })
  }
}
</script>
