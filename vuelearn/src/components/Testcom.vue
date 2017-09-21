<template>
  <div>

    <div >this is template body</div>

    <div v-for="item in list">{{'姓名:'+item.name+'   体重'+item.weight +'特别体重:'+weight}} </div>
  <button v-on:click="addItem">addItem</button>

    <a v-bind:href="baiduLink">go to Baidu now~</a>

  </div>
</template>


<script>

  import Vue from 'vue'
  export default {
    props:['weight'],
    methods:{
      addItem() {
        Vue.set(this.list,1,{
          name:'肥肥罗昊旻',
          weight:'90'
        })
        console.log('hahahhaa')
        this.list.push(this.fatHat);
      }
    },
    data() {
      return {
        msg: 'hello vue',
        baiduLink:'www.baidu.com',
        list:[
          {
            name:'jiahao',
            weight:'50'
          },
          {
            name:'luohaomin',
            weight:'60'
          }
        ],
        fatHat:{
          name:'feifeiHatt',
          weight:'999'
        }
      }
    }
  }
</script>

<style>
  body {
    background-color: white;
  }
</style>
