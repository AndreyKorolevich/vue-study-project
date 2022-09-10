<template>
  <ul>
    <learning-resources v-for="res in storedResources" :key="res.id" :title="res.title" :description="res.description"
                        :link="res.link">

    </learning-resources>
  </ul>
</template>

<script>

import LearningResources from "@/components/learning-resources/LearningResources";

export default {
  components: {
    LearningResources
  },
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'Learn Vue by Official guide',
          link: 'https://vuejs.org/guide/introduction.html'
        },
        {id: 'google', title: 'Google', description: 'Learn Vue by Google ...', link: 'https://www.google.com/'}
      ]
    }
  }
}
</script>