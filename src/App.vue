<template>
  <div id="app">
    <FormTest></FormTest>
    父组件钱数：{{nmy}}
    <!-- <HelloWorld
      :value="nmy"
      @update:val="(val)=>this.nmy=val"
    ></HelloWorld> -->

    <HelloWorld :value.sync="nmy"></HelloWorld>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import FormTest from './components/form/index.vue'


export default {
  name: 'App',
  components: {

    HelloWorld, FormTest
  },
  methods: {
    // change(value) {
    //   this.nmy = value
    // }
  },
  data() {
    return {
      nmy: 100

    }
  },
  created() {
    console.log('father created', '')
  },
  beforeMount() {
    console.log(' father beforeMount', '')
  },
  mounted() {
    console.log(' father mounted', '')
  }

}


// class Bus {
//   constructor() { this.callbacks = {}; }
//   $on(name, fn) {
//     this.callbacks[name] = this.callbacks[name] || [];
//     this.callbacks[name].push(fn);
//   }
//   $emit(name, args) {
//     if (this.callbacks[name]) {
//       this.callbacks[name].forEach(cb => cb(args))
//     }
//   }
// }
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
</style>
