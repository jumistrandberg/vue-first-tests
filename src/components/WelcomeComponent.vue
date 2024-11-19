<script setup>
// Import the `ref` function from Vue to create reactive variables
import { ref } from "vue";

// Create reactive variables `name` and `age` to hold user input values
// Reactive variables are wrapped in `ref` so their values are automatically updated in the DOM
let name = ref(""); // Initially empty
let age = ref("");  // Initially empty

// Create a reactive variable `show` to control the visibility of the button
let show = ref(true); // Initially set to `true`, so the button is visible

// Function to handle form submission
function onSubmit() {
  // Template literals (`) allow for interpolation of values within strings
  alert(`Hej ${name.value}, du är ${age.value} år gammal!`); // Interpolation with `${}` inserts reactive variable values
  name.value = ""; // Clear the `name` field after submission
  age.value = "";  // Clear the `age` field after submission
}

// Function to toggle visibility of the button
function toggleShow() {
  show.value = false; // Update the reactive `show` variable to hide the button
}
</script>

<template>
  <!-- Interpolation is used here to display static text dynamically in the DOM -->
  <h1>Welcome to lektion 1 av Vuekursen hehe</h1>
  
  <!-- Form element with `@submit.prevent` directive -->
  <!-- `@submit.prevent` prevents the default form submission and instead calls the `onSubmit` function -->
  <form @submit.prevent="onSubmit">
    <h3>Skapa Profil</h3>
    
    <!-- Input field for `name` -->
    <!-- `v-model` creates two-way data binding with the `name` ref -->
    <!-- This means the input field updates the `name` ref and vice versa -->
    <input type="text" v-model="name" placeholder="Namn tack" />

    <!-- Input field for `age` -->
    <!-- `v-model` binds the input field to the `age` ref -->
    <input type="number" v-model="age" placeholder="Ålder tack" />

    <!-- Submit button for the form -->
    <button type="submit">Skicka</button>
  </form>

  <div>
    <!-- Conditional rendering with `v-if` -->
    <!-- The button is only rendered in the DOM if `show` is true -->
    <!-- `@click` listens for a click event and calls the `toggleShow` function -->
    <button v-if="show" @click="toggleShow">Click me</button>
  </div>
</template>

<style>
/* Styling the h1 element */
h1 {
  font-weight: 400; /* Set font weight to normal */
  color: yellowgreen; /* Set text color */
}
</style>
