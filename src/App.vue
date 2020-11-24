<template>
  <div id="app">
    <div class="column is-half is-offseet-one-quarter">
       <div v-for="(poke,index) in pokemons" :key="index">
      <Pokemon :name="poke.name" :url="poke.url" :num="index+1" />
      <br>
    </div>
    </div>
   
  </div>
</template>

<script>
import axios from 'axios'
import Pokemon from './components/Pokemon'
export default {
  name: 'App',
  data(){
    return{
      pokemons: []
    }
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res =>{
      this.pokemons = res.data.results
    })
  },
  components: {
    Pokemon
  }
}
</script>


<style scoped>
  *{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

 
</style>
