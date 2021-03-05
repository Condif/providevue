<template>
  <div id="app">
    <Menu
      :alfaSort="alfaSort"
      :dateSort="dateSort"
      :sortPostsByCategory="sortPostsByCategory"
      :categories="categories"
    />
    <Posts :posts="posts" :filteredPosts="filteredPosts" />
  </div>
</template>

<script>
import Menu from "./components/Menu.vue";
import Posts from "./components/Posts.vue";

import axios from "axios";

export default {
  name: "App",
  components: {
    Menu,
    Posts,
  },
  data() {
    return {
      categories: [],
      posts: [],
      filteredPosts: [],
      isAlfaDescending: false,
      isDateDescending: false,
    };
  },
  methods: {
    dateSort() {
      this.isDateDescending = !this.isDateDescending;
      let tempPosts = [];
      if (this.filteredPosts.length !== 0) {
        tempPosts = [...this.filteredPosts];
      } else {
        tempPosts = [...this.posts];
      }

      if (this.isDateDescending) {
        tempPosts.sort((a, b) => {
          if (a.date < b.date) {
            return 1;
          }
          if (a.date > b.date) {
            return -1;
          }
          return 0;
        });
      } else {
        tempPosts.sort((a, b) => {
          if (a.date < b.date) {
            return -1;
          }
          if (a.date > b.date) {
            return 1;
          }
          return 0;
        });
      }

      if (this.filteredPosts.length !== 0) {
        this.filteredPosts = tempPosts;
      } else {
        this.posts = tempPosts;
      }
    },
    alfaSort() {
      this.isAlfaDescending = !this.isAlfaDescending;
      let tempPosts = [];
      if (this.filteredPosts.length !== 0) {
        tempPosts = [...this.filteredPosts];
      } else {
        tempPosts = [...this.posts];
      }

      if (this.isAlfaDescending) {
        tempPosts.sort((a, b) => {
          if (a.title.rendered < b.title.rendered) {
            return 1;
          }
          if (a.title.rendered > b.title.rendered) {
            return -1;
          }
          return 0;
        });
      } else {
        tempPosts.sort((a, b) => {
          if (a.title.rendered < b.title.rendered) {
            return -1;
          }
          if (a.title.rendered > b.title.rendered) {
            return 1;
          }
          return 0;
        });
      }

      if (this.filteredPosts.length !== 0) {
        this.filteredPosts = tempPosts;
      } else {
        this.posts = tempPosts;
      }
    },

    sortPostsByCategory(category) {
      let tempPosts = [...this.posts];
      let categoryPostList = [];
      tempPosts.forEach((post) => {
        if (post.categories.find((x) => x === category.id) === category.id) {
          categoryPostList.push(post);
        }
      });

      categoryPostList.sort((a, b) => {
        if (a.title.rendered < b.title.rendered) {
          return -1;
        }
        if (a.title.rendered > b.title.rendered) {
          return 1;
        }
        return 0;
      });
      this.filteredPosts = categoryPostList;
    },
  },
  async created() {
    await axios
      .get("http://ftest.dev3.provideit.se/wp-json/wp/v2/categories")
      .then((res) => {
        this.categories = res.data;
      })
      .catch((err) => console.log(err));
    await axios
      .get(
        "http://ftest.dev3.provideit.se/wp-json/wp/v2/posts?orderby=title&order=asc"
      )
      .then((res) => {
        this.posts = res.data;
        console.log(res.data);
      })
      .catch((err) => console.log(err));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

ul {
  list-style-type: none;
}
</style>
