<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2 v-bind:class="[classA,{'redfont':hasError}]"  v-bind:style="linkCss">Essential Links</h2>

    <Testcom :weight="weight"></Testcom>

    <button v-on:click="changeWeight">changeHattWeight</button>


    <p v-if="isShowPartA">PartA</p>
    <p v-else>没有数据啦</p>


    <a v-show="!isShowPartA">PartB</a>

  </div>
</template>

<script>

  import Testcom from './Testcom.vue'
  export default {
  methods:{
    changeWeight(){
      this.weight='999999999'
      this.linkCss.color='black'
      this.isShowPartA=!this.isShowPartA;
    }
  },
  name: 'hello',
  data () {
    return {
      classA:'bluefont',
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
  components:{
    Testcom
  }
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
</style>
