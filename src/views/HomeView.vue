<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <p>測試千分位：一共 {{ $thousandths(1000) }} 元</p>
    <button type="button" class="btn btn-primary-color">測試 Bootstrap 自訂變數</button>

    <!-- Button trigger modal -->
  <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
    測試 Bootstrap 樣式、JS 載入
  </button>

  <!-- Modal -->
  <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          ...
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
          <button type="button" class="btn btn-primary">Save changes</button>
        </div>
      </div>
    </div>
  </div>

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
