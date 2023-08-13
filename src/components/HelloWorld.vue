<script setup>
import { ref } from 'vue'

// Used to toggle visibility of elements
const visible1 = ref(true)
const visible2 = ref(false)

const items = ref([{ message: 'first entry' }, { message: 'second entry' }])
const numerals = ref([6, 7, 3, 2, 12])

// blank variables that will update live based on input
const contactName = ref('')
const contactEmail = ref('')
const contactQuery = ref('')
const contactMessage = ref('')
</script>

<template>
  <div class="grand-box">
    <!-- State starts visible1 = true, button toggles -->
    <button @click="visible1 = !visible1">Toggle If/Else</button>
    <br>
    <!-- Visible if visible1 = true -->
    <div class="box" v-if="visible1">
      <h1>V-If</h1>
      <p>This section will, as far as the viewer is concerned, to swap places with another when a button is pressed.</p>
    </div>
    <!-- Visible if visible1 != true -->
    <div class="box" v-else>
      <h1>V-Else</h1>
      <p>This box only appears after the button has been pressed, since it and the if box are connected by the switch.</p>
    </div>
  </div>

  <div class="grand-box">
    <!-- visible2 = false by default, toggles state-->
    <button @click="visible2 = !visible2">Toggle Show</button>
    <br>
    <div class="box box2" v-show="visible2">
      <h1>V-Show</h1>
      <p>This box is always visible in the DOM, appearing and vanishing on click</p>
    </div>
  </div>
  
  <div class="grand-box">
    <div class="box box2">
      <h1>V-For</h1>
      <!-- Print all strings in array items as a list -->
      <li v-for="x in items">
        {{  x.message }}
      </li>
      <!-- Print numerals from 1 through 4, with spaces -->
      <span v-for='n in 4'>{{ n + ' '}}</span>
    </div>
  </div>

  <div class="grand-box">
    <div class="box">
      <h1>V-For + V-If</h1>
      <!-- Prints values from array numerals only if value > 5 -->
      <div v-for="x in numerals">
        <li v-if="x > 5">
          {{ x }}
        </li>
      </div>
      <br>
      <!-- Prints values from array only if value is greater/equal to 3 and less than 8 -->
      <div v-for="x in numerals">
        <li v-if="x >=3 && x < 8">
          {{ x }}
        </li>
      </div>
    </div>
  </div>

  <div class="grand-box">
    <div class="box box3">
      <!-- Contact form logging all input as variables -->
      <h1>V-Model</h1>
        <h2>Contact Us!</h2>
        <p>Name:</p>
        <input v-model="contactName">
        <p>Email:</p>
        <input v-model="contactEmail">
        <p>Query Type:</p>
        <!-- Drop down selection, one option only -->
        <select v-model="contactQuery">
          <option disabled value=""></option>
          <option>Bug Report</option>
          <option>Suggestion</option>
          <option>Other Queries</option>
        </select>
        <p>Message:</p>
        <textarea v-model="contactMessage"></textarea>
    </div>
  </div>

  <div class="grand-box">
    <div class="box box3">
      <!-- Displays the output of the contact form -->
      <h1>Received Report</h1>
      <p><b>Sendee: </b>{{ contactName }}</p>
      <p>{{ '<' + contactEmail + '>' }}</p>
      <p><b>Query Type: </b>{{ contactQuery }}</p>
      <hr>
      <p><b>Message:</b></p>
      <!-- Display message with line formatting intact -->
      <p style="white-space: pre-line;">{{ contactMessage }}</p>
    </div>
  </div>
  
</template>

<style>
.grand-box {
  border: 3px dashed rgb(207, 205, 200);
  padding: 20px;
  margin: 5px;
}

.box {
  border: 2px solid rgb(235, 122, 171);
  padding: 20px;
  margin: 5px;
}

.box2 {
  border-color: rgb(77, 218, 218);
}

.box3 {
  border-color: rgb(189, 231, 96)
}
/* Correcting for css in base.css */
b {
  font-weight: bold;
}
</style>
