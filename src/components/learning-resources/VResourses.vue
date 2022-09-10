<template>
  <v-card>
    <v-button @click="setSelectedTab('store-resources')" :mode="storedResButtonMode">Stored Resources</v-button>
    <v-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Resources</v-button>
  </v-card>
  <component :is="selectedTab"></component>
</template>

<script>
import VCard from "@/components/UI/VCard";
import VButton from "@/components/UI/VButton";
import StoreResources from "./StoreResoursces";
import AddResource from "./AddResource";


export default {
  name: 'v-resources',
  components: {VButton, VCard, StoreResources, AddResource},
  data() {
    return {
      selectedTab: 'store-resources',
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
  },
  provide() {
    return {
      resources: this.storedResources
    }
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'store-resources' ? null : 'flat'
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat'
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab
    }
  }
}
</script>