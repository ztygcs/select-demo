<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>自定义下拉框组件</h1>
    <div class="mainDiv">
      <Selects :list='letter' class="childDiv" @checkItem = "letterchecked"></Selects>
      <Selects :list='number' class="childDiv" @checkItem = "numberchecked"></Selects>
    </div>
  </div>
</template>

<script>
//组件的引入
import Selects from './components/Selects.vue'

export default {
  name: 'App',
  data(){
    return{
      letter:['a','b','c','d','e'],
      number:[1,2,3,4,5,6,7,8,9]
    }
  },
  components: {//组件的声明
    Selects
  },
  methods:{
    //输出选择的项
    letterchecked:function(index){
      console.log('下拉框1选中项：{index:'+index+','+'value:'+this.letter[index]+'}')
    },
    numberchecked:function(index){
      console.log('下拉框2选中项：{index:'+index+','+'value:'+this.number[index]+'}')
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

/* 父组件布局 */
.mainDiv {
    margin-top: 2%;
}
.childDiv{
    float: left;
}
</style>
