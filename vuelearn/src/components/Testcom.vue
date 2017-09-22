<template>
  <div>
     <!--自定义指令-->
    <p v-color="'red'">this is template body</p>

    <slot name="header">no header</slot>
    <p> luan qi ba zao</p>
    <slot name="footer">no footer</slot>

    <div v-for="item in list">{{'姓名:'+item.name+'   体重'+item.weight +'特别体重:'+weight}} </div>
  <button v-on:click="addItem">addItem</button>

    <a v-bind:href="baiduLink">go to Baidu now~</a>

    <!--<input v-on:keydown.enter="onkeydowns">-->


    <input v-model="myValue" type="text">
    我的值:{{myValueWithoutNumber }}


    <input v-model="myBox" type="radio" value="apple">
    <input v-model="myBox" type="radio" value="banana">
    <input v-model="myBox" type="radio" value="watermelon">

    {{myBox}}

    <!--<select v-model="selection">-->
      <!--<option v-for="item in selectionOptions" v-bind:value="item.value">{{item.name}}</option>-->
    <!--</select>-->
    <!--{{selection}}-->

    <VSelect @my-select="mySelectEvent" :selectionOptions="selectionOptions" number=78></VSelect>

    <button v-on:click="emitMyEvent">子组件按钮触发回调事件</button>

  </div>
</template>


<script>

  import Vue from 'vue'
  import VSelect from './VSelect.vue'
  export default {
    props:['weight'],
//    props:{
//      'weight':[String] //增加类型判断
//    },

//    自定义指令
    directives:{
      color:function (el,binding) {
        el.style.color = binding.value;
      }
    },


    components:{VSelect},
    watch:{
      myValue:(newVAL,oldVal)=>{
        console.log('new:'+newVAL+'---old:'+oldVal);
        alert(newVAL)
      }
    },
    computed:{
      myValueWithoutNumber(){
        return this.myValue.replace(/\d/g,'')
      }
    },
    methods:{

      mySelectEvent(paramsValues){
        console.log('choose :'+paramsValues)
      },

      emitMyEvent(){
        this.$emit('my-event',this.msg)
      },

      addItem() {
        Vue.set(this.list,1,{
          name:'肥肥罗昊旻',
          weight:'90'
        })
        console.log('hahahhaa')
        this.list.push(this.fatHat);
      },
      onkeydowns(){
        console.log("on key down")
      }
    },
    data() {
      return {
        selectionOptions:[
          {
            name:'apple',
            value:1
          },{
            name:'xxxbann',
            value:2
          },{
            name:'ggggg',
            value:3
          }
        ]
        ,

        myBox:[],
        myValue:'',
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
