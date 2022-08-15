<template>
  <img src="./assets/Pokemon.svg" alt="" :style="imageStyles">
  <label for="select-pokemon">Select type</label>
  <select name="select-pokemon" v-model="selected">
  <option v-for="option in options" :value="option.value">
    {{ option.text }}
  </option>
</select>

<div>
  <ul>
    <li v-for="pokemon in pokemons" :key="pokemon.name">
      <img src="./assets/Pokemon.svg" alt="">
      <div class="pokemon-info">
        <p>{{ pokemon.name }} </p>
        <p>{{ pokemon.classfication }}</p>
      </div>
    </li>
  </ul>
  <hr />
  <button @click="onButtonClick">Button</button>
</div>
</template>

<script setup>
import { ref, computed } from 'vue'

const selected = ref(null)
let imageStyles = ref({
  width: '100%',
  height: 'auto',
  opacity: 1,
  transition: 'all 0.2s ease-in-out',
  transform: 'none'
})
const options = ref([
  { text: 'Normal', value: null },
  { text: 'Grass', value: 'grass' },
  { text: 'Water', value: 'water' },
  { text: 'Fire', value: 'fire' }
])

const onButtonClick = () => {
  imageStyles.value = {
    ...imageStyles.value,
    opacity: imageStyles.value.opacity === 0 ? 1 : 0,
    transform: imageStyles.value.transform === 'translateY(100%)' ? 'none' : 'translateY(100%)'
  }
}

const checkTransform = () => {
  console.log('🍎 transfor', imageStyles.value);
}

const pokemons = computed(() => {

  if(selected.value) return API_DATA[selected.value]

  return [...API_DATA['grass'], ...API_DATA['fire'], ...API_DATA['water']]
})

const API_DATA = {
  "grass": [
    {
      "name": "Bulbasaur",
      "classfication": "Seed Pokémon",
      "height_m": 0.7,
      "weight_kg": 6.9,
      "hp": 45,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/bulbasaur.png"
    },
    {
      "name": "Ivysaur",
      "classfication": "Seed Pokémon",
      "height_m": 1,
      "weight_kg": 13,
      "hp": 60,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/ivysaur.png"
    },
    {
      "name": "Venusaur",
      "classfication": "Seed Pokémon",
      "height_m": 2,
      "weight_kg": 100,
      "hp": 80,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/venusaur.png"
    },
    {
      "name": "Bellsprout",
      "classfication": "Flower Pokémon",
      "height_m": 0.7,
      "weight_kg": 4,
      "hp": 50,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/bellsprout.png"
    },
    {
      "name": "Weepinbell",
      "classfication": "Flycatcher Pokémon",
      "height_m": 1,
      "weight_kg": 6.4,
      "hp": 65,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/weepinbell.png"
    },
    {
      "name": "Victreebel",
      "classfication": "Flycatcher Pokémon",
      "height_m": 1.7,
      "weight_kg": 15.5,
      "hp": 80,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/victreebel.png"
    }
  ],
  "water": [
    {
      "name": "Squirtle",
      "classfication": "Tiny Turtle Pokémon",
      "height_m": 0.5,
      "weight_kg": 9,
      "hp": 44,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/squirtle.png"
    },
    {
      "name": "Wartortle",
      "classfication": "Turtle Pokémon",
      "height_m": 1,
      "weight_kg": 22.5,
      "hp": 59,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/wartortle.png"
    },
    {
      "name": "Blastoise",
      "classfication": "Shellfish Pokémon",
      "height_m": 1.6,
      "weight_kg": 85.5,
      "hp": 79,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/blastoise.png"
    },
    {
      "name": "Poliwag",
      "classfication": "Tadpole Pokémon",
      "height_m": 0.6,
      "weight_kg": 12.4,
      "hp": 40,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/poliwag.png"
    },
    {
      "name": "Poliwhirl",
      "classfication": "Tadpole Pokémon",
      "height_m": 1,
      "weight_kg": 20,
      "hp": 65,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/poliwhirl.png"
    },
    {
      "name": "Poliwrath",
      "classfication": "Tadpole Pokémon",
      "height_m": 1.3,
      "weight_kg": 54,
      "hp": 90,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/poliwrath.png"
    },
    {
      "name": "Psyduck",
      "classfication": "Duck Pokémon",
      "height_m": 0.8,
      "weight_kg": 19.6,
      "hp": 50,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/psyduck.png"
    },
    {
      "name": "Golduck",
      "classfication": "Duck Pokémon",
      "height_m": 1.7,
      "weight_kg": 76.6,
      "hp": 80,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/golduck.png"
    }
  ],
  "fire": [
    {
      "name": "Charmander",
      "classfication": "Lizard Pokémon",
      "height_m": 0.6,
      "weight_kg": 8.5,
      "hp": 39,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/charmander.png"
    },
    {
      "name": "Charmeleon",
      "classfication": "Flame Pokémon",
      "height_m": 1.1,
      "weight_kg": 19,
      "hp": 58,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/charmeleon.png"
    },
    {
      "name": "Charizard",
      "classfication": "Flame Pokémon",
      "height_m": 1.7,
      "weight_kg": 90.5,
      "hp": 78,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/charizard.png"
    },
    {
      "name": "Growlithe",
      "classfication": "Puppy Pokémon",
      "height_m": 0.7,
      "weight_kg": 19,
      "hp": 55,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/growlithe.png"
    },
    {
      "name": "Arcanine",
      "classfication": "Legendary Pokémon",
      "height_m": 1.9,
      "weight_kg": 155,
      "hp": 90,
      "image": "https://img.pokemondb.net/sprites/x-y/normal/arcanine.png"
    }
  ]
}
</script>

<style lang="scss" scoped>

 select {
  height: 2rem;
  width: 70%;
  margin-bottom: 2rem;
 }

 label {
  display: block;
 }

 ul {
  list-style: none;
  height: 20rem;
  width: 20rem;
  overflow: hidden;
  overflow-y: scroll;
  margin: 0;
  padding: 0;
 }

 li {
  margin-bottom: 1rem;
  padding: .22rem;
  border: solid 2px rgba(0,0,0,.7);
  display: flex;
  align-items: center;

  img {
    margin-left: .25rem;
    margin-right: 1rem;
    height: 4rem;
    width: 4rem;
  }

  p {
    margin: 0;
  }
 }

 button {
  width: 100%;
  background-color: blue;
  color: white;
  border-radius: .1rem;
 }

 hr {
  margin: 0 -1rem 1rem -1rem;
 }

 .pokemon-info {
  display: flex;
  flex-direction: column;
  align-items: baseline;
 }

</style>
