<template>
  <v-dialog v-if="inputIsInvalid" title="Invalid Input" @close-dialog="confirmError">
    <template #default>
      <p>Unfortunately, at least one input is invalid.</p>
      <p>Please check all the inputs and make sure you enter at least a few characters into each input field</p>
    </template>
    <template #actions>
      <v-button @click="confirmError" @keyup.esc="confirmError">Ok</v-button>
    </template>
  </v-dialog>
  <v-card>
    <form @submit.prevent="createResource">
      <div class="form-control">
        <label for="title">Title</label>
        <input v-model="title" id="title" name="title" type="text">
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea v-model="description" id="description" name="description" rows="3"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input v-model="link" id="link" name="link" type="url" />
      </div>
      <div class="form-control">
        <v-button type="submit">Add Resource</v-button>
      </div>
    </form>
  </v-card>
</template>

<script>
import VCard from "@/components/UI/VCard";
import VButton from "@/components/UI/VButton";
import VDialog from "@/components/UI/VDialog";

export default {
  name: 'add-resource',
  components: {VDialog, VButton, VCard},
  data() {
    return {
      title: '',
      link: '',
      description: '',
      inputIsInvalid: false
    }
  },
  inject: {
    addResource: {
      type: Function
    }
  },
  methods: {
    createResource() {
      const resource = {
        id: this.title.trim().toLowerCase().split(' ').join('-'),
        title: this.title.trim(),
        link: this.link.trim(),
        description: this.description.trim()
      }

      if(!resource.title || !resource.link || !resource.description){
        this.inputIsInvalid = true
        return
      }

      this.addResource(resource)
      this.resetData()
    },
    resetData() {
      this.title = ''
      this.link = ''
      this.description = ''
    },
    confirmError() {
      this.inputIsInvalid = false
    }
  }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>