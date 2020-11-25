<template>
  <div id="app">
    <div class="column is-half is-offseet-one-quarter">
      <h4 class="is-size-3">Pokedex</h4>
      <input type="text" placeholder="buscar pokemon pelo nome" v-model="busca" class="input is-rounded">
       <button class="button is-info is-outlined" id="buscaBtn" @click="buscar">Buscar</button>
       <div v-for="(poke,index) in filteredPokemons" :key="poke.url">
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
      pokemons: [],
      filteredPokemons:[],
      busca: ''
    }
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res =>{
      this.pokemons = res.data.results
      this.filteredPokemons = res.data.results
    })
  },
  components: {
    Pokemon
  },

  methods:{
    buscar: function(){
      this.filteredPokemons = this.pokemons //reseta a lista de pokemons filtrados
      if(this.busca == '' || this.busca == ' '){
        this.filteredPokemons = this.pokemons
      }else{
          this.filteredPokemons = this.pokemons.filter(pokemon => pokemon.name == this.busca)
      }
    }
  },
  //computed:
    /*
    resultadoBusca: function(){
      if(this.busca == '' || this.busca == ' '){
        return this.pokemons;
      }else{
        return this.pokemons.filter(pokemon => pokemon.name == this.busca)
      }
    }
  }
  */
}
</script>


<style scoped>
  *{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

 #app{
   font-family: Avenir, Helvetica, Arial, sans-serif;
   -webkit-font-smoothing: antialiased;
   -moz-osx-font-smoothing: grayscale;
   text-align: center;
   color: #2c3e50;
   margin-top: 60px;
   display: flex;
   flex-direction: column;
   align-items: center;
 }

 #buscaBtn{
   margin-top: 5px;
 }
</style>
