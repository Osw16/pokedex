<template>
  <div class="pokedex">
    <h2>pokedex</h2>
    <pokedex-screen :pokemonData="loadData"/>

    <input type="text" class="form-control" v-model="pokemon" />
    <button @click="getPokemon">Buscar</button>
    <img class="card-img-top rounded mx-auto mt-2" :src="imageUrl"/>
  </div>
</template>

<script>
import PokedexScreen from './PokedexScreen.vue'

export default {
  name: 'Pokedex',
  components: {
    PokedexScreen
  },

  data () {
    return {
      imageUrl: null,
      error: false,
      loading: true,
      pokemon: 150,
      loadData: [],
      pokemonId: Math.floor(Math.random() * 806 + 1).toString()
    }
  },

  created () {
    this.getPokemon()
    // console.log('created pokedex')
  },

  methods: {
    // Mientras se llama a la API, loading es verdadero,
    // cuando la API nos da una respuesta, el estado se actualiza
    // dependiendo de si todo fue un éxito o un fracaso
    getPokemon () {
      const imgPokemon = `https://github.com/PokeAPI/sprites/blob/master/sprites/pokemon/${this.pokemon}.png?raw=true`
      this.imageUrl = imgPokemon
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon}`)
      // fetch('https://pokeapi.co/api/v2/pokemon/charmander')
        .then((res) => res.json())
        .then((data) => {
          const response = [data].map(d => ({ name: d.name, exp: d.base_experience, type: d.types[0].type.name }))
          this.loadData = response[0]
          this.loading = false
          // console.log(this.loadData)
          console.log(state.pokemon)
        }
        )
    }
  }
}
</script>
