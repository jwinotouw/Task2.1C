<template>
  <div id="app" class=“container”>
    <h1>Vue 3 Concepts</h1>
    <h2>Conditional Rendering</h2>

  <div class=“card”>
    <p v-if="showMessage">ENGINE STATUS: ONLINE</p>
    <p v-else>ENGINE STATUS: OFFLINE</p>
    <button @click="toggleMessage">Toggle Engine ON/OFF</button>
  </div>

  <div class=“card”>
    <p v-show="showGreeting">SYSTEM STATUS: ALL SYSTEM NORMAL</p>
    <button @click="toggleGreeting">System Status HIDE/SHOW</button>
  </div>

  <div class=“card”>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
    <p v-if="items.length === 0">No items to display.</p>
    <input type="text" v-model="newItem" placeholder="Enter a new item" />
    <button @click="addItem">Add Item</button>
  </div>

    <h2>Form Input Handling</h2>
    <form @submit.prevent="submitForm" class=“card”>
      <label for="name">Name:</label>
      <input type="text" id="name" v-model.trim="name" />
      <label for="email">Email:</label>
      <input type="email" id="email" v-model.lazy="email" />
      <label for="message">Message:</label>
      <textarea id="message" v-model="message"></textarea>
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    // data
    const showMessage = ref(true);
    const showGreeting = ref(true);
    const items = ref(["Lamborghini", "Ferrari", "Bentley"]);
    const newItem = ref("");
    const name = ref("");
    const email = ref("");
    const message = ref("");

    // methods
    const toggleMessage = () => {
      showMessage.value = !showMessage.value;
    };

    const toggleGreeting = () => {
      showGreeting.value = !showGreeting.value;
    };

    const addItem = () => {
      if (newItem.value) {
        items.value.push(newItem.value);
        newItem.value = "";
      }
    };

    const submitForm = () => {
      alert(`Name: ${name.value}\nEmail: ${email.value}\nMessage: ${message.value}`);
      name.value = "";
      email.value = "";
      message.value = "";
    };

    // return
    return {
      showMessage,
      showGreeting,
      items,
      newItem,
      name,
      email,
      message,
      toggleMessage,
      toggleGreeting,
      addItem,
      submitForm,
    };
  },
};
</script>

<style scoped>
h1 {
  color: rgb(0, 255, 179); text-align: center;
}

h2 {
  color: green; margin-top: 20px; margin-bottom: 10px;
}

.container { 
  max-width: 800px; margin: 0 auto; font-family: Arial, sans-serif;
}

.card {
  border: 1px solid black; border-radius: 10px; padding: 20px; box-shadow: 5px 5px 10px gray; margin-bottom: 20px;
}

label {
  display: block; margin-bottom: 5px;
}

input, textarea {
  width: 100%; padding: 10px; border: none; outline: none; border-radius: 5px; box-sizing: border-box; font-size: 16px;
}

button {
  display: block; margin-top: 10px; padding: 10px; width: 100%; background-color: rgb(0, 255, 179); color: rgb(0, 0, 0); border: none; outline: none; border-radius: 5px; font-size: 16px; cursor: pointer;
}

button:hover {
  background-color: rgb(0, 139, 81);
}

</style>