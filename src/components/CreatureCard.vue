<template>
  <hr />
  <div v-for="[key, value] in keyValuePairs" :key="key">
    <h5 style="margin-bottom: 0px">{{ key }}</h5>
    <p style="margin-top: 2px">{{ value }}</p>
  </div>
  <hr />
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
  setup(props) {
    const keyValuePairs = Object.entries(props.creature);

    return { keyValuePairs };
  },
};
</script>

<style>
</style>
