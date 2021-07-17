<template>
  <h1>The Reaction timer game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  
    <Block v-if='isPlaying' :delay='delay' @gameEnd="End"/> 
    <Results v-if="showResults" :ReactionTime="ReactionTime"/>

</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';
export default {
  
  name: 'App',
  components: {
    Block, 
    Results,
  },
  data(){
    return {
      isPlaying : false,
      delay : null,
      ReactionTime:null,
      showResults:false,
    }
 
  },
  
  methods:{
    start(){
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000
      this.showResults = false
    },
    End(ReactionTime){
      this.ReactionTime = ReactionTime
      this.showResults = true
      this.isPlaying = false
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
</style>
