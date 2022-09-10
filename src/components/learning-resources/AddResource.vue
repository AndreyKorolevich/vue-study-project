<template>
  <v-card>
    <form>
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type=text/>
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" name="description" row="3"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <textarea id="link" name="link" type="url"></textarea>
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

export default {
  name: 'add-resource',
  components: {VButton, VCard},
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