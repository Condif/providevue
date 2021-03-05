<template>
  <div class="container">
    <div class="content">
      <template v-if="filteredPosts.length === 0">
        <div class="posts" v-for="(post, index) in posts" v-bind:key="index">
          <div class="date">
            <h5>{{(post.date.slice(0,10))}}</h5>
            <h5>{{(post.date.slice(11,21))}}</h5>

          </div>
          <h3 class="title">{{ post.title.rendered }}</h3>
          <p>
            <span class="htmlContent" v-html="post.excerpt.rendered"></span>
          </p>
        </div>
      </template>
      <template v-else>
        <div
          class="posts"
          v-for="(post, index) in filteredPosts"
          v-bind:key="index"
        >
           <div class="date">
            <h5>{{(post.date.slice(0,10))}}</h5>
            <h5>{{(post.date.slice(11,21))}}</h5>

          </div>
          <h3 class="title">{{ post.title.rendered }}</h3>
          <p>
            <span class="htmlContent" v-html="post.excerpt.rendered"></span>
          </p>
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
  box-shadow: 0 0 3pt 2pt black;
  width: clamp(35ch, 50%, 90ch);
}

.posts {
  margin: 1rem 0 1rem 0;
}

.title {
  margin: 1rem 0 1rem 0;
  font-size: clamp(1rem, 2.2vw, 3rem);
}

p {
  font-size: clamp(1rem, 1.6vw, 3rem);
}
.date {
  display: flex;
}

h5 {
  margin-right: 1rem;
}
</style>
