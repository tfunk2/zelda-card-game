<template>
  <h5>Name</h5>
  <p>{{ creature.name }}</p>
</template>

<script>
export default {
  name: "CreatureCard",
  props: {
    creature: {
      type: String,
      required: true,
    },
  },
  setup() {
    return {};
  },
};
</script>

<style>
</style>
