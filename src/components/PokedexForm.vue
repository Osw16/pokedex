<template>
  <form class="pokemon-form" v-on:submit={handleSubmit}>
    <input
      class="pokemon-input"
      type="text"
      name="pokemon"
      v-model="pokemonName"
      placeholder="Busca tu pokemon"
      autocomplete="off"/>
    <input
      type="submit"
      class="pokemon-btn"
      value=""
    />
  </form>
  <div>
    <input type="text" class="form-control" v-model="pokecito" />
    <button @click="fetchPoke">Buscar</button>
  </div>
</template>

<script>
export default {
  name: 'PokedexForm',

  data () {
    return {
      pokemonName: ''
    }
  },

  methods: {
    fetchPoke () {
      console.log('pokecito!')
    },
    search (e) {
      e.preventDefault()
      const pokemonName = this.pokemonName
      const newPokemonId = window.isNaN(parseInt(pokemonName)) ? pokemonName.toLowerCase() : pokemonName
      this.$emit('submit', newPokemonId)
    },
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
