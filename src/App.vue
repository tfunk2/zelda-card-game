<template>
  <h1>Zelda Card Game</h1>
  <h3>Food Creatures:</h3>
  <CreatureCard
    v-for="creature in foodCreatures"
    :key="creature.id"
    :creature="creature"
  />
</template>

<script>
import { ref } from "@vue/reactivity";
import { onMounted, computed } from "@vue/runtime-core";
import CreatureCard from "./components/CreatureCard.vue";

export default {
  name: "App",
  components: {
    CreatureCard,
  },
  setup() {
    const allZeldaData = ref();

    const fetchAndSetZeldaData = async () => {
      await fetch("https://botw-compendium.herokuapp.com/api/v2/all")
        .then((resp) => resp.json())
        .then(({ data }) => (allZeldaData.value = data));
    };

    const allCreatures = computed(() => {
      if (allZeldaData.value) {
        return allZeldaData.value.creatures;
      }
    });

    const foodCreatures = computed(() => {
      if (allCreatures.value) {
        return allCreatures.value.food;
      }
    });

    /**
     * This is working as intended and setting allZeldaData on mount
     */
    onMounted(() => {
      fetchAndSetZeldaData();
    });

    return {
      allCreatures,
      allZeldaData,
      foodCreatures,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}
</style>
