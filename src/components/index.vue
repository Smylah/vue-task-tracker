<template>
  <Header :title="title"/>
  <h1>{{message}}</h1>
  <button @click="swap">swap</button>
</template>

<script>
import Header from "./Header.vue"

export default {
    name: 'HelloWorld',
    components: {
      Header,
    },
    data() {
      return {
        message: 'message',
        title: 'task tracker'
      }
    },
    methods: {
      swap() {
        if(this.message === "message"){
          return this.message = "hill"
        }else if (this.message === "hill"){
          return this.message = "message"
        }
      }
    }
  
}
</script>

<style>

</style>