<template>
  <div id="app">
    <fact v-if="fact" :user="fact"></fact>
     

  </div>
</template>

<script>
import Fact from './components/Fact'
export default {
  name: 'app',
  components: {
    Fact
  },
  data(){
    return {
      fact: null
    }
  },
   mounted(){
    this.axios.get('http://188.225.47.187/api/cats/random-fact.php').then((response)=>{
      this.fact = response.data.results[0]
    }).catch(err=>{
      console.log('error', err)
    })

  },  

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
