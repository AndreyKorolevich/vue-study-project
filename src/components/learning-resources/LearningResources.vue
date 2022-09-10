<template>
  <li>
    <v-card>
      <header>
        <h3>{{ title }}</h3>
        <v-button @click="deleteResource" :mode="'flat'">Delete</v-button>
      </header>
      <p>{{ description }}</p>
      <nav>
        <a :href="link">View Resource</a>
      </nav>
    </v-card>
  </li>
</template>

<script>
import VCard from "@/components/UI/VCard";
import VButton from "@/components/UI/VButton";

export default {
  name: 'learning-resources',
  components: {VCard, VButton},
  props: {
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    link: {
      type: String,
      required: true
    }
  },
  methods: {
    deleteResource() {
      console.log('kek')
    }
  }
}
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>