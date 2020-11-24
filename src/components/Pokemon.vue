<template>
    <div>
        <h1> </h1>
        <h2>{{type}}</h2>
        <small>{{url}}</small>


<div class="card">
  <div class="card-image">
    <figure class="image is-4by3">
      <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
      <div class="media-left">
        <figure class="image is-48x48">
          <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
        </figure>
      </div>
      <div class="media-content">
          <p class="title is-4">{{ num }} - {{name | upper }}</p>
          <p class="subtitle is-6">{{ this.pokemon.type }}</p>
      </div>
    </div>

    <div class="content">
     
    </div>
  </div>
</div>


    </div>
</template>

<script>
import axios from 'axios'
export default {
    created: function(){
        axios.get(this.url).then(res => {
            this.pokemon.type = res.data.types[0].type.name
            this.pokemon.front = res.data.sprites.front_default
            this.pokemon.back = res.data.sprites.back_default
        })
    },
    data(){
        return{

        }
    },
    props: {
        num: Number,
        name: String,
        url: String
    },
    filters:{
        upper: function(value){
            var newName = value[0].toUpperCase() + value.slice(1)
            return newName
        }
    }
}

</script>

<style lang="stylus">

</style>