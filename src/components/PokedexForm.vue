<template>
  <!-- <form
    class="pokemon-form"
    v-on:submit="
      {
        handleSubmit;
      }
    "
  > -->
    <!-- <input
      class="pokemon-input"
      type="text"
      name="pokemon"
      v-model="pokemonName"
      placeholder="Busca tu pokemon"
      autocomplete="off"
    /> -->
    <!-- <input type="submit" class="pokemon-btn" value="" /> -->
  <!-- </form> -->
  <div>
    <!-- <input type="text" class="form-control" v-model="pokemonId" /> -->
    <!-- <input class="form-control mr-sm-2" v-model="search" id="navBarSearchInput" type="search" placeholder="Search" aria-label="Search" /> -->
    <!-- <button @click="getPokemon">Buscar</button> -->
    <!-- <h2>pokemon: {{pokemon}}</h2> -->
  </div>
</template>

<script>
export default {
  name: 'PokedexForm',

  data () {
    return {
      pokemonName: '',
      pokemon: '',
      search: ''
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
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonId}`)
        .then((res) => res.json())
        .then((data) => {
          this.pokemon = data.results
          this.loading = false
          console.log('pokemon', data.name)
        })
    },
    fetchPoke () {
      console.log('pokecito!')
    },
    // search (e) {
    //   e.preventDefault()
    //   const pokemonName = this.pokemonName
    //   const newPokemonId = window.isNaN(parseInt(pokemonName))
    //     ? pokemonName.toLowerCase()
    //     : pokemonName
    //   this.$emit('submit', newPokemonId)
    // },
    handleSubmit (pokemonId) {
      console.log('handle')
      if (pokemonId !== '') {
        this.error = false
        this.loading = true
        this.pokemonId = pokemonId
        this.getPokemon()
        return
      }
      this.error = true
    }
  }
}
</script>
