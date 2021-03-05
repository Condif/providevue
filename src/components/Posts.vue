<template>
  <div>
    <template v-if="filteredPosts.length === 0">
      <div v-for="(post, index) in posts" v-bind:key="index">
        <h3>{{ post.title.rendered }}</h3>
        <h3>{{ post.date }}</h3>
      </div>
    </template>
    <template v-else>
      <div v-for="(post, index) in filteredPosts" v-bind:key="index">
        <h3>{{ post.title.rendered }}</h3>
        <h3>{{ post.date }}</h3>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "Posts",
  props: ["posts", "filteredPosts"],
};
</script>

<style scoped></style>
