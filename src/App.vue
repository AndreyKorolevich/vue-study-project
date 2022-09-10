<template>
  <v-header :title="'RememberMe'"></v-header>
  <v-resourses></v-resourses>
</template>

<script>

import VHeader from "@/components/layouts/VHeader";
import VResourses from "@/components/learning-resources/VResourses";

export default {
  components: {
    VResourses,
    VHeader,
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>