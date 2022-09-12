<template>
  <ul>
    <li :class="{active: modelValue === getRatings.POOR}">
      <button type="button" @click="activate(getRatings.POOR)">Poor</button>
    </li>
    <li :class="{active: modelValue === getRatings.AVERAGE}">
      <button type="button" @click="activate(getRatings.AVERAGE)">Average</button>
    </li>
    <li :class="{active: modelValue === getRatings.GREAT}">
      <button type="button" @click="activate(getRatings.GREAT)">Great</button>
    </li>
  </ul>
</template>

<script>


  import { AVERAGE, GREAT, POOR } from '../constant';

export default {
  name: 'rating-control',
  props: ['modelValue'],
  emits: ['update:modelValue'],
  methods: {
    activate(option) {
      this.$emit('update:modelValue', option)
    },
  },
  computed: {
    getRatings() {
      return {
        POOR,
        AVERAGE,
        GREAT
      }
    }
  }
};
</script>

<style scoped>
.active {
  border-color: #a00078;
}

.active button {
  color: #a00078;
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>