<template>
  <ul>
    <learning-resources v-for="res in resources" :key="res.id" :title="res.title" :description="res.description"
                        :link="res.link" :id="res.id">

    </learning-resources>
  </ul>
</template>

<script>

import LearningResources from "@/components/learning-resources/LearningResources";

export default {
  name: 'store-resources',
  components: {
    LearningResources
  },
  inject: {
    resources: {
      type: Array,
      required: true
    },
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>