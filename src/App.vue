<template>
  <div id="app">
    <div class="containerSquare">
       <div class="mainSquare" :class="(color==true) ? 'blueColor' : 'purpleColor'">
      <p class="text">Please click the button in order to change the background color!</p>
    </div>
    </div>
   
    <div class="containerButton">
      <button v-on:click="changeColor" > Change color</button>
    </div>

   


  </div>
</template>

<script>


export default {
  name: 'App',
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  
}
.mainSquare{
  background: #00AEEF;
  width: 600px;
  height:500px;
  display: flex;
  justify-content: center;
  align-items: center;
  

}
.text{
  color:white;
  font-size: 25px;
}
.buttonContainer{
  display: flex;
  justify-content: center;
  padding-top:1000px

}
.blueColor{
  background-color: #00AEEF;
}
.purpleColor{
  background-color: #CB6CE6;
}
.containerSquare {
    display: flex;
    justify-content: center;
}
button {
    margin-top: 40px;
    height: 50px;
    background: black;
    color:white;
    padding:15px;
    border: none;
   
}
</style>

