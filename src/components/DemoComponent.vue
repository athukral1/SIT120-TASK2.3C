<template>
  <div class="demo-container">
    <!-- 1. Template Syntax -->
    <div>
      <p class="title">{{ message }}</p>
      <div class="html-container" v-html="rawHtml"></div>
      <div :id="elementId"></div>
      <p class="result">{{ 2 + 2 }}</p>
    </div>

    <!-- 2. Methods -->
    <div class="section">
      <button class="button" @click="sayHello">Say Hello</button> <!-- Method Handlers -->
      <button class="button" @click="customClickHandler">Custom Click</button>
    </div>

    <!-- 3. Reactivity Fundamentals -->
    <div class="section">
      <p class="title">Reactivity Fundamentals</p>
      <p>{{ reactiveValue }}</p>
    </div>

    <!-- 4. Computed Properties -->
    <div class="section">
      <p class="title">Computed Properties</p>
      <p>{{ computedValue }}</p>
    </div>

    <!-- 5. Class and Style Bindings -->
    <div class="section">
      <p class="title">Class and Style Bindings</p>
      <div :class="{ 'active': isHighlighted }"></div> <!-- Binding HTML class -->
      <div :style="{ color: textColor, fontSize: textSize }"></div> <!-- Binding Inline Styles -->
    </div>

    <!-- 6. List Rendering -->
    <div class="section">
      <p class="title">List Rendering</p>
      <ul>
        <!-- a. v-for with an Object -->
        <li v-for="(item, index) in itemsToShow" :key="index">{{ item.name }}</li>
        <!-- b. v-for with a Range -->
        <li v-for="n in 5" :key="n">{{ n }}</li>
      </ul>
    </div>

    <!-- 7. Event -->
    <div class="section">
      <p class="title">Event</p>
      <button class="button" @click="inlineClickHandler">Inline Click</button> <!-- Inline Handlers -->
    </div>

    <!-- 8. Form -->
    <div class="section">
      <p class="title">Form</p>
      <!-- Customized input fields -->
      <div class="form-container">
        <input type="text" v-model.trim="textInput" placeholder="Your Name" class="custom-input" /> <!-- v-model with .trim -->
        <input type="checkbox" v-model="checkboxValue" />
        <input type="radio" v-model="radioValue" value="option1" />
        <select v-model="selectedOption" class="custom-select">
          <option value="option1">Option 1</option>
          <option value="option2">Option 2</option>
        </select>
        <textarea v-model.trim="textareaValue" placeholder="Your Message" class="custom-textarea"></textarea>
      </div>
    </div>

    <!-- 9. Watcher -->
    <div class="section">
      <p class="title">Watcher</p>
      <input type="text" v-model="textInput" placeholder="Watch me" class="custom-input" />
    </div>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';

// Data
const message = ref('Hello, Vue!');
const rawHtml = ref('<span>Raw HTML</span>');
const elementId = ref('myElement');

// Reactivity Fundamentals
const reactiveValue = ref(0);

// Computed Properties
const items = ref([
  { id: 1, name: 'Item 1', showDetails: true },
  { id: 2, name: 'Item 2', showDetails: false },
]);
const computedValue = computed(() => items.value.length);

// Class and Style Bindings
const isHighlighted = ref(false);
const textColor = ref('blue');
const textSize = ref('20px');

// Methods
const sayHello = () => {
  alert('Hello from Vue!');
};
const customClickHandler = () => {
  alert('Custom click handler');
};

// Event
const inlineClickHandler = () => {
  alert('Inline click handler');
};

// Form
const textInput = ref('');
const checkboxValue = ref(false);
const radioValue = ref('');
const selectedOption = ref('option1');
const textareaValue = ref('');

// Computed property to filter items to show
const itemsToShow = computed(() => {
  return items.value.filter((item) => item.showDetails);
});

// Watcher
watch(textInput, (newValue, oldValue) => {
  console.log(`textInput changed from ${oldValue} to ${newValue}`);
});
</script>

<style scoped>
/* Add component-specific styles here */
.demo-container {
  margin: 20px;
  padding: 20px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 1.5rem;
  margin-bottom: 10px;
  color: #333;
}

.section {
  margin: 20px 0;
}

.button {
  background-color: #007bff; /* Updated button background color */
  color: #fff; /* Updated button text color */
  border: none;
  border-radius: 5px;
  padding: 8px 16px;
  cursor: pointer;
  transition: background-color 0.3s ease-in-out;
}

.button:hover {
  background-color: #0056b3; /* Updated button hover background color */
}

/* Add more component-specific styles as needed */
</style>