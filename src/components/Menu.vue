<template>
  <div class="container">
    <div class="ulCategories">
      <ul v-for="category in categories" v-bind:key="category.id">
        <li>
          <button @click="sortPostsByCategory(category)">
            {{ category.name }}
          </button>
        </li>
      </ul>
    </div>
    <div class="sortContainer">
      <h3>Sort:</h3>
      <button class="sortButton" @click="alfaSort()">Alfabetisk</button>
      <button class="sortButton" @click="dateSort()">Datum</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Menu",
  props: ["categories", "sortPostsByCategory", "alfaSort", "dateSort"],
};
</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: clamp(20ch 60%, 40ch);
  flex-direction: column;
}
.ulCategories {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.ulCategories li {
  margin: 1rem 1rem 1rem 1rem;
  width: clamp(20ch 60%, 40ch);
}
button {
  
  width: 8rem;
  height: 2rem;
  color: white;
  background: rgba(0, 0, 255, 0.767);
  border-radius: 1rem;
  border: none;
  opacity: 80%;
  
}

li button {
    outline: none;
}

button:hover {
  opacity: 100%;
  cursor: pointer;
}

.sortButton {
  background: none;
  color: black;
  border: black solid 1px;
  margin: 0 1rem 0 1rem;
  outline: none;
}
.sortButton:focus {
        box-shadow: 0 0 3pt 2pt blue;
    }

.sortContainer {
    display: flex;
    margin-top: 2rem;
}

@media screen and (max-width: 600px) {
  .sortContainer {
    flex-direction: column;
    
  }
  .sortButton {
      margin-top: 1rem;
  }
}
</style>
