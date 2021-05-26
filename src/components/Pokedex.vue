<template>
  <div class="pokedex">
    <div class="pokedex-left">
      <div class="pokedex-left-top">
        <div class="light is-sky is-big in-animated" />
        <div class="light is-red" />
        <div class="light is-yellow" />
        <div class="light is-green" />
      </div>
      <div class="pokedex-screen-container">
        <pokedex-screen />
        <img
          v-if="error"
          src="../assets/error.gif"
          alt="Hubo un error buscando tu pokemon"
          class="pokedex-no-screen"
        />
      </div>
      <div class="pokedex-left-bottom">
        <div class="pokedex-left-bottom-lights">
          <div class="light is-blue is-medium" />
          <div class="light is-green is-large" />
          <div class="light is-orange is-large" />
        </div>
        <!-- <pokedex-form v-on:submit="handleSubmit($event)" /> -->
        <pokedex-form  />
      </div>
    </div>
    <!-- <div class="pokedex-right-front" /> -->
    <!-- <div class="pokedex-right-back" /> -->
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
      pokemonId: Math.floor(Math.random() * 806 + 1).toString()
    }
  },

  created () {
    this.getPokemon()
  },

  methods: {
    // Mientras se llama a la API, loading es verdadero,
    // cuando la API nos da una respuesta, el estado se actualiza
    // dependiendo de si todo fue un éxito o un fracaso
    getPokemon () {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonId}`)
        .then((res) => res.json())
        .then((data) => {
          this.pokemon = data
          this.loading = false
        }
        )
    }
  }
}
</script>
