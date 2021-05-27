
<template>
  <div class="pokedex-screen">
    <!-- <Stat/> -->
    <!-- <h2>{{output}}</h2> -->
    <h2>{{pokemonData.type}}</h2>
  </div>
</template>

<script>
// import Stat from './Stat.vue'
export default {
  name: 'PokedexScreen',
  props: ['pokemonData'],
  components: {
    // Stat
  },
  data () {
    return {
      output: ''
    }
  },
  created () {
    return this.getData()
  },
  methods: {
    getData () {
      console.log('mew', this.pokemonData)
    }
  }

}
</script>
