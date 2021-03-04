<template>
    <div class="container">
        <div class="ulCategories">
            <ul  v-for="category in categories" v-bind:key="category.id">
                <li><button @click="sortPostsByCategory(category)">{{category.name}}</button></li>
            </ul>
        </div>
        <h3>Sort:</h3>
        <button @click="alfaSort()">Alfabetisk</button>
        <button @click="dateSort()">Datum</button>
    </div>
</template>

<script>
export default {
  name: 'Menu',
  props: ['categories', "sortPostsByCategory", "alfaSort", "dateSort"],
}
</script>

<style scoped>
    .container {
        border: solid 1px green;
        display: flex;
        align-items: center;
        justify-content: center;
        height: 5rem;
    }
    .ulCategories {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .ulCategories li {
        margin: 0 1rem 0 1rem;
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

    button:hover {
        opacity: 100%;
        cursor: pointer;
    }
</style>

