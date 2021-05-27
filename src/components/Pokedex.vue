<template>
  <div class="pokedex">
    <h2>pokedex</h2>
    <pokedex-screen :pokemonData="loadData"/>
    <pokedex-form/>
    <input type="text" class="form-control" v-model="pokemon" />
    <button @click="getPokemon">Buscar</button>
    {{pokeOutput}}
  </div>
</template>

<script>
import PokedexScreen from './PokedexScreen.vue'
import PokedexForm from './PokedexForm.vue'

export default {
  name: 'Pokedex',
  components: {
    PokedexScreen,
    PokedexForm
  },

  data () {
    return {
      error: false,
      loading: true,
      pokemon: null,
      loadData: [],
      pokeOutput: [],
      pokemonId: Math.floor(Math.random() * 806 + 1).toString()
    }
  },

  created () {
    // this.getPokemon()
    // console.log('created pokedex')
  },

  methods: {
    // Mientras se llama a la API, loading es verdadero,
    // cuando la API nos da una respuesta, el estado se actualiza
    // dependiendo de si todo fue un éxito o un fracaso
    getPokemon () {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon}`)
      // fetch('https://pokeapi.co/api/v2/pokemon/charmander')
        .then((res) => res.json())
        .then((data) => {
          this.loadData = [data].map(d => ({ name: d.name, exp: d.base_experience }))
          this.pokeOutput = data.name
          this.loading = false
          console.log(this.loadData)
        }
        )
    }
  }
}
</script>
