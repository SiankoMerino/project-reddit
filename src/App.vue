<template>
  <div id="app">
    <NavBarComponent @delete-all-posts="deleteAllPosts"
    @reload-posts="fetchPosts"/>
    <div class="main-container">
      <CardComponent 
      v-for="(post, index) in posts" 
      :key="index" 
      :post="post"
      :index="index"
      @remove-post="removePost" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import NavBarComponent from './components/nav-bar.vue'
import CardComponent from './components/cardComponent.vue'

export default {
  name: 'App',
  components: {
    NavBarComponent,
    CardComponent
  },
  data() {
    return {
      posts: []
    };
  },
  mounted() {
    this.fetchPosts();
  },
  methods: {
    async fetchPosts() {
      try {
        const response = await axios.get('https://run.mocky.io/v3/c3b0e56b-b5af-4903-8246-a9b9fc12d3d0');
        this.posts = response.data.posts;
      } catch (error) {
        console.error('Error fetching posts:', error);
      }
    },
    removePost(index) {
      this.posts.splice(index, 1);
    },
    deleteAllPosts() {
      this.posts = [];
    }
  }
}
</script>

<style>

body, html {
  background-color: #0E1113;
  color: #FFFFFF;
}

* {
  padding: 0;
  margin: 0;
  outline: none;
  border: none;
  box-sizing: border-box;
  font-family: sans-serif;
}

.main-container {
  display: flex;
  align-items: center;
  flex-direction: column;
  height: 100vh;
  padding-top: 65px;
}

@media (min-width: 320px) and (max-width: 768px) {
  .main-container {
    padding-top: 75px;
  }
}
</style>
