<template>
  <div class="container">
    <div class="content">
      <template v-if="filteredPosts.length === 0">
        <div class="posts" v-for="(post, index) in posts" v-bind:key="index">
          <h5>{{ post.date }}</h5>
          <h3>{{ post.title.rendered }}</h3>
          
        </div>
      </template>
      <template v-else>
        <div class="posts" v-for="(post, index) in filteredPosts" v-bind:key="index">
          <h5>{{ post.date }}</h5>
          <h3>{{ post.title.rendered }}</h3>
          
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: "Posts",
  props: ["posts", "filteredPosts"],
};
</script>

<style scoped>
.container {
  display: grid;
  place-items: center;
  margin-top: 2rem;
}

.content {
  width: clamp(23ch 50%, 46ch);
  display: flex;
  flex-direction: column;
  padding: 1rem;
  border: 0.5px solid black;
  
}

.posts {
  margin: 1rem 0 1rem 0
}
</style>
