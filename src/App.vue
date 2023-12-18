<script setup>
import { ref } from "vue";

const showModal = ref(false);
const newNoteInput = ref("");
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
        <button class="add-note">Add note</button>
        <button class="close" @click="showModal = false">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Note {{ showModal }}</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="card-container">
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis
            mollitia voluptatem iste blanditiis itaque nesciunt.
          </p>
          <p class="date">18th/12/2023</p>
        </div>
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis
            mollitia voluptatem iste blanditiis itaque nesciunt.
          </p>
          <p class="date">18th/12/2023</p>
        </div>
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Facilis
            mollitia voluptatem iste blanditiis itaque nesciunt.
          </p>
          <p class="date">18th/12/2023</p>
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
</style>
