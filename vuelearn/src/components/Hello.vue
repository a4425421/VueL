<template>
  <div class="hello">
    <transition name="fade">
      <h1 v-show="showTag">{{ msg }}</h1>
    </transition>

    <button v-on:click="showTag =! showTag">show</button>

    <h2 v-bind:class="[classA,{'redfont':hasError}]"  v-bind:style="linkCss">Essential Links</h2>

    <testCom :weight="weight"  @my-event="onTestcomEvent">
      <p slot="header"> 嘻嘻嘻嘻header</p>
      <span slot="footer">fish footer</span>
    </testCom>

    <button v-on:click="changeWeight">changeHattWeight</button>
    <!--keep alive 可以切换的时候缓存起来-->

    <keep-alive>
    <p :is="comToRender" :weight="weight"  @my-event="onTestcomEvent"></p>
    </keep-alive>

    <p v-if="isShowPartA">PartA</p>
    <p v-else>没有数据啦</p>


    <a v-show="!isShowPartA">PartB</a>

  </div>
</template>

<script>

  import testCom from './Testcom.vue'
  import  vSelect from  './VSelect.vue'
  export default {
    components:{
      testCom,
      vSelect
    },
  methods:{
    changeWeight(){
      this.weight='999999999'
      this.linkCss.color='black'
      this.isShowPartA=!this.isShowPartA;

      this.comToRender =this.comToRender==='v-select'?'test-com':'v-select'

    },
    onTestcomEvent(message){
      console.log('组件Testcom回调'+message)
    }
  },
  name: 'hello',
  data () {
    return {
      classA:'bluefont',
      comToRender:'test-com',
      showTag:true,
      hasError:true,
      isShowPartA:false,
      classStr:{
        redfont:true,
        bluefont:false
      },
      msg: 'Welcome to Your Vue.js Addpp',
      message:'keke',
      weight:'',
      linkCss:{
        'color':'red',
        'font-size':'20px'
      }
    }
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a ,p{
  color: #42b983;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 1.5s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in below version 2.1.8 */ {
  opacity: 0
}
</style>
