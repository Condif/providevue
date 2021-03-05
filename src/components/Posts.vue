<template>
  <div class="container">
    <div class="content">
      <template v-if="filteredPosts.length === 0">
        <div class="posts" v-for="(post, index) in posts" v-bind:key="index">
          <h5>{{ post.date }}</h5>
          <h3 class="title" >{{ post.title.rendered }}</h3>
          <p>{{post.content.rendered}} </p>
          
        </div>
      </template>
      <template v-else>
        <div class="posts" v-for="(post, index) in filteredPosts" v-bind:key="index">
          <h5>{{ post.date }}</h5>
          <h3 class="title">{{ post.title.rendered }}</h3>
          <p>{{post.content.rendered}} </p>
          
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
  display: flex;
  flex-direction: column;
  padding: 1rem;
  border: 0.5px solid black;
  width: clamp(35ch, 50%, 70ch)
  
}

.posts {
  margin: 1rem 0 1rem 0
}

.title {
  margin: 1rem 0 1rem 0;
  font-size: clamp(1rem, 2.2vw, 3rem); 
}

p {
  font-size: clamp(1rem, 1.6vw, 3rem); 
}
</style>
