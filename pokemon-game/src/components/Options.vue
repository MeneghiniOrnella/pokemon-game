<template>
    <div class="options-container">
        <ul class="vertical buttons">
            <li v-for="pokemon in pokemons" :key="pokemon.id" @click="$emit('selection', pokemon.id)" class="inverted red fluid ui button">
                {{ pokemon.name }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        pokemons: {
            type: Array,
            required: true
        }
    },
    methods: {
        hi(){
            //this.$emit
        }
    }
}
</script>

<style scoped>
ul{
    list-style: none;
}
.button{
    background-color: blue;
}
/* li{
    background-color: rgb(165, 199, 14);
    border-radius: 5px;
    border: 1px solid rgba(0,0,0,0.2);
    cursor: pointer;
    margin-bottom: 10px;
    width: 250px;
}
li:hover{
    background-color: rgba(41, 150, 223, 0.5);
} */
.options-container{
    display: flex;
    justify-content: center;
}
</style>