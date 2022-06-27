<template>
  <div class="hello">
    <div v-if="!pokemon" class="ui segment">
      <div class="ui active dimmer">
        <div class="ui massive text loader">Loading</div>
      </div>
      <p></p>
    </div>
    <div v-else>
      <h1>¿Quién es este Pokemón?</h1>
      <!--<Picture :pokemon-id="105" :showPokemon="true" />-->
      <Picture :pokemon-id="pokemon.id" :show-pokemon="showPokemon" />
      <Options :pokemons="pokemonArr" @selection="checkAnswer" />
    </div>
    <template v-if="showAnswer">
      <h2 class="fade-in">{{ message }}</h2>
      <button @click="newGame" class="ui toggle button active">New game</button>
    </template>
  </div>
</template>

<script>
import Options from '@/components/Options.vue';
import Picture from '@/components/Picture.vue';
import getOptions from '@/helpers/getOptions';

export default {
    components: { Options, Picture },
    data() {
      return{
        pokemonArr:  [],
        pokemon:     null,
        showPokemon: false,
        showAnswer:  false,
        message:     ''
      }
    },
    methods: {
      async mixPokemonArray(){
        this.pokemonArr = await getOptions()
        const rndInt = Math.floor(Math.random()*4)
        this.pokemon = this.pokemonArr[rndInt]
      },
      checkAnswer(selectedId){
        this.showPokemon = true
        this.showAnswer  = true
        if(selectedId === this.pokemon.id){
          this.message = `Correcto, era ${ this.pokemon.name }`
        }else{
          this.message = `Incorrecto, aún te falta para ser un maestro pokemon, era ${ this.pokemon.name }`
        }
      },
      newGame(){
        this.showPokemon = false
        this.showAnswer  = false
        this.pokemonArr  = []
        this.pokemon     = null
        this.mixPokemonArray()
      }
    },
    mounted() {
      this.mixPokemonArray()
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>