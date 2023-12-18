<script setup>
import { ref } from "vue";

const showModal = ref(false);
const newNoteInput = ref("");
const notes = ref([]);
function getRandomColor() {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}

const errorMessage = ref("");

const onAdd = () => {
  if (newNoteInput.value.length < 10) {
    return (errorMessage.value = "Note must be more than 10 Characters!");
  }
  notes.value.push({
    id: Math.floor(Math.random() * 1000000),
    text: newNoteInput.value,
    date: new Date(),
    backgroundColor: getRandomColor(),
  });
  showModal.value = false;
  newNoteInput.value = "";
  errorMessage.value = "";
};

const onClose = () => {
  showModal.value = false;
  newNoteInput.value = "";
  errorMessage.value = "";
};
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea
          v-model="newNoteInput"
          name="noteInput"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <p v-if="errorMessage" class="error-text">{{ errorMessage }}</p>
        <button class="add-note" @click="onAdd()">Add note</button>
        <button class="close" @click="onClose()">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Note</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="card-container">
        <div
          v-for="note in notes"
          :key="note.id"
          class="card"
          :style="{ backgroundColor: note.backgroundColor }"
        >
          <p class="main-text">
            {{ note.text }}
          </p>
          <p class="date">{{ note.date.toLocaleDateString("en-US") }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scooped>
main {
  height: 100vh;
  width: 100vw;
}

.container {
  max-width: 1000px;
  padding: 10px;
  margin: auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  font-weight: bold;
  color: white;
  margin-bottom: 25px;
  font-size: 75px;
}

button {
  border: none;
  padding: 10px;
  width: 50px;
  height: 50px;
  cursor: pointer;
  border-radius: 100%;
  color: black;
  background-color: blanchedalmond;
  font-size: 20px;
}

.card {
  width: 225px;
  height: 225px;
  background-color: khaki;
  padding: 10px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
}

.main-text {
  color: black;
  font-size: 12px;
}

.date {
  color: black;
  font-weight: bold;
  font-size: 13px;
}

.card-container {
  display: flex;
  flex-direction: row;
}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  border-radius: 15px;
  width: 750px;
  background-color: white;
  border-radius: 10px;
  padding: 15px;
  position: relative;
  display: flex;
  flex-direction: column;
  border: 10px;
  border-color: black;
}

.modal textarea {
  padding: 10px 10px;
  font-size: 20px;
  width: 100%;
  border-radius: 15px;
  cursor: pointer;

  margin-top: 15px;
}

.modal button {
  padding: 10px 10px;
  font-size: 20px;
  width: 100%;
  border-radius: 15px;
  cursor: pointer;

  margin-top: 15px;
}
.add-note {
  background-color: greenyellow;
}

.close {
  background-color: red;
}

.error-text {
  color: red;
  font-weight: bold;
}
</style>
