<template>
  <div id="app">
    
    <calculator/>
   


  </div>
</template>

<script>
import calculator from './components/calculator.vue'

export default {
  name: 'App',
  components:{calculator},
  data () {
      return {
        color: false,
        
        
      }
    },
    methods:{
      changeColor(){
         this.color = this.color == true ? false : true
      }
      
    }
  

}
</script>

<style>

</style>

