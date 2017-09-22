<template>
  <div>
    <select v-model="selection" v-on:click="onSelectListener">
      <option v-for="item in selectionOptions" v-bind:value="item.value">{{item.name}}</option>
    </select>
    {{number}}
  </div>
</template>


<script>


  export default {
    props: ['selectionOptions','number'],
    watch: {
      selection: (val) => {
        console.log('直接wacht:' + val)
      }
    },
    methods: {
      onSelectListener() {
        this.$emit('my-select', this.selection)
      }
    },
    data() {
      return {
        selection: null,
        msg: 'hello vue'
      }
    },


  }
</script>

<style>
  body {
    background-color: #ffffff;
  }
</style>
