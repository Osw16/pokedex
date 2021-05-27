<template>
  <div class="pokedex-screen">
    <h2>Hello Ash!</h2>
    <h2>imagen:</h2>
    <img class="card-img-top rounded mx-auto mt-2" :src="imageUrl"/>
    <h2>name:</h2>
    <h2>Descrip:</h2>
    <!-- <input type="text" class="form-control" v-model="pokeIndex" />
    <button @click="getUrl">Buscar</button> -->
  </div>
</template>

<script>
// import Stat from './Stat.vue'
export default {
  name: 'PokedexScreen',
  components: {
  },
  data () {
    return {
      pokeIndex: [],
      imageUrl: null
    }
  },
  mounted () {
    this.getUrl()
  },

  methods: {
    getUrl () {
      // const imgPokemon = `https://github.com/PokeAPI/sprites/blob/master/sprites/pokemon/${this.pokeIndex}.png?raw=true`
      const imgPokemon = 'https://github.com/PokeAPI/sprites/blob/master/sprites/pokemon/1.png?raw=true'
      this.imageUrl = imgPokemon
      // console.log('imgPokemon', imgPokemon)
    }
  }
}
</script>
