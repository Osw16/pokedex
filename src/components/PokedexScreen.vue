
<template>
  <div class="pokedex-screen">
    <Stat/>
    <!-- <h2>{{output}}</h2> -->

  </div>
</template>

<script>
import Stat from './Stat.vue'
export default {
  name: 'PokedexScreen',
  props: ['pokemonData'],
  components: {
    Stat
  },
  data () {
    return {
      output: ''
    }
  },
  mounted () {
    this.output = this.pokemonData
  }

}
</script>
