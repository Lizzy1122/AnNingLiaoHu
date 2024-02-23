<template>
  <div id="search_container">
    <input type="text" placeholder="请输入关键词" v-model="inputObject.userInput" id="inputObject.inputId">
    <button id="searchBtn" @click="send">search</button>
  </div>
</template>

<script>
import bus from '@/Bus/bus.js'
export default {
  data(){
    return{
      inputObject:{
        userInput:'',
        inputId:'searchInput'
      }

    }
  },
  methods:{
    send(){
      bus.$emit('shareUserInput',this.inputObject)
      console.log(this.inputObject)
    }
  },
  mounted() {
    this.send()
  }
}
</script>

<style lang="less" scoped>
#search_container{
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
  input{
    height: 30px;
    width: 300px;
  }
  #searchBtn{
    height: 36px;
    width: 100px;
    background-color: aliceblue;
  }
}
</style>
