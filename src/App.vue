<script setup>
import Card from './components/card.vue'
import { ref } from 'vue'

const cardData = ref([
  { id: 1, number: '#0001', name: 'Bulbasaur', type: 'Grass, Poison', description: 'A strange seed was planted on its back at birth. The plant sprouts and grows with this Pokémon.' },
  { id: 2, number: '#0002', name: 'Ivysaur', type: 'Grass, Poison', description: 'When the bulb on its back grows large, it appears to lose the ability to stand on its hind legs.' },
  { id: 3, number: '#0003', name: 'Venusaur', type: 'Grass, Poison', description: 'The plant blooms when it is absorbing solar energy. It stays on the move to seek sunlight.' },
  { id: 4, number: '#0004', name: 'Charmander', type: 'Fire', description: 'The flame that burns at the tip of its tail is an indication of its health. The hotter and bigger the flame, the healthier the Pokémon.' },
  { id: 5, number: '#0005', name: 'Charmeleon', type: 'Fire', description: 'When it swings its burning tail, it elevates the temperature to unbearably high levels.' },
  { id: 6, number: '#0006', name: 'Charizard', type: 'Fire, Flying', description: 'Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.' },
  { id: 7, number: '#0007', name: 'Squirtle', type: 'Water', description: 'After birth, its back swells and hardens into a shell. It powerfully sprays foam from its mouth.' },
  { id: 8, number: '#0008', name: 'Wartortle', type: 'Water', description: 'It is said to live 10,000 years. Its furry tail is popular as a symbol of longevity.' },
  { id: 9, number: '#0009', name: 'Blastoise', type: 'Water', description: 'A brutal Pokémon with pressurized water jets on its shell. They are used for high-speed tackles.' },
  { id: 10, number: '#0010', name: 'Caterpie', type: 'Bug', description: 'For protection, it releases a horrible stench from the antenna on its head to drive away enemies.' },
  { id: 11, number: '#0011', name: 'Metapod', type: 'Bug', description: 'The shell is hard, but it is also fragile. It can be broken with a single punch.' },
  { id: 12, number: '#0012', name: 'Butterfree', type: 'Bug, Flying', description: 'In battle, it flaps its wings at high speed to release highly toxic dust into the air.' }
])

const searchString = defineModel()
const filteredData = ref(cardData.value)

function search() {
  const searchTerm = searchString.value.toLowerCase()
  filteredData.value = cardData.value.filter(pokemon => {
    return (
      pokemon.id.toString() === searchTerm ||
      pokemon.number.toLowerCase().includes(searchTerm) ||
      pokemon.name.toLowerCase().includes(searchTerm) ||
      pokemon.type.toLowerCase().includes(searchTerm)
    )
  })
}

</script>

<template>
  <header>
    <div class="navbar">
      <div class="navbar-title">
        <h1>Pokédex</h1>
      </div>
      <div class="navbar-search">
        <input type="text" placeholder="Search Pokémon..." v-model="searchString" @keyup="search"/>
      </div>
    </div>
    </header>
  <main>
    <div class="cards">
      <Card v-for="(data, index) in filteredData" :key="data.id" :data="data" />
    </div>
  </main>
</template>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  width: 100vw;
  height: 10vh;
  background-color: #f8f8f8;
  padding: 0 20px;

  margin-bottom: 20px;
}

.navbar-title {
  font-size: 24px;
}

.navbar-search {
  display: flex;
  justify-content: center;
  align-items: center;
}

.navbar-search input {
  width: 300px;
  height: 30px;
  border-radius: 5px;
  border: 1px solid #ccc;
  padding: 5px;

  font-size: 16px;
  transition: border-color 0.3s;
}

main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100vw;
}

.cards {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 30px;
  width: 100vw;
}
</style>
