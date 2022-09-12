<template>
  <form @submit.prevent="submitForm">
    <div class="form-control" :class="{invalid: checkInvalid}">
      <label for="user-name">Your Name</label>
      <input id="user-name" name="user-name" type="text" v-model.trim="inputName" @blur="validateName"/>
      <p v-if="checkInvalid">Please enter a valid name</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input id="age" name="age" type="number" v-model="inputAge"/>
    </div>
    <div class="form-control">
      <label for="source">How did you hear about us?</label>
      <select id="source" name="source" v-model="selectSource">
        <option v-for="option in options" :value="option.value" :key="option.value">
          {{ option.text }}
        </option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div v-for="checkbox in checkboxes" :key="checkbox.value">
        <input :id="`interest-${checkbox.value.toLowerCase()}`" name="interest" type="checkbox" :value="checkbox.value"
               v-model="checkedInterest"/>
        <label :for="`interest-${checkbox.value.toLowerCase()}`">{{ checkbox.text }}</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div v-for="radio in radios" :key="radio.value">
        <input :id="`how-${radio.value.toLowerCase()}`" name="how" type="radio" :value="radio.value"
               v-model="checkedType"/>
        <label :for="`how-${radio.value.toLowerCase()}`">{{ radio.text }}</label>
      </div>
    </div>
    <div class="form-control">
      <rating-control v-model="rating"></rating-control>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
import {
  BLOGS,
  GOOGLE,
  INVALID,
  NEWS,
  NEWSPAPER,
  NOTHING,
  OTHER,
  PENDING,
  TUTORIALS,
  VALID,
  VIDEO,
  WOM
} from "../constant";
import RatingControl from "./RatingControl";

export default {
  components: {RatingControl},
  data() {
    return {
      inputName: '',
      inputAge: null,
      selectSource: WOM,
      checkedInterest: [],
      checkedType: '',
      nameValidity: PENDING,
      rating: null,
      options: [
        {text: 'Google', value: GOOGLE},
        {text: 'Word of mouth', value: WOM},
        {text: 'Newspaper', value: NEWSPAPER}
      ],
      checkboxes: [
        {text: 'News', value: NEWS},
        {text: 'Tutorials', value: TUTORIALS},
        {text: 'Nothing', value: NOTHING},
      ],
      radios: [
        {text: 'Video Courses', value: VIDEO},
        {text: 'Blogs', value: BLOGS},
        {text: 'Other', value: OTHER},
      ]
    }
  },
  methods: {
    submitForm() {
      const data = {
        name: this.inputName,
        age: this.inputAge,
        source: this.selectSource,
        interests: this.checkedInterest,
        type: this.checkedType,
        rating: this.rating
      }
      this.resetData()
      console.log(data)
    },
    validateName() {
      if (this.inputName === '') {
        this.nameValidity = INVALID
      } else {
        this.nameValidity = VALID
      }
    },
    resetData() {
      this.inputName = ''
      this.inputAge = null
      this.selectSource = WOM
      this.checkedInterest = []
      this.checkedType = ''
      this.nameValidity = PENDING
      this.rating = null
    }
  },
  computed: {
    checkInvalid() {
      return this.nameValidity === INVALID
    }
  }
}
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

.form-control.invalid input {
  border-color: red;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>