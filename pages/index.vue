<template>
  <div class="container">
    <div class="wrapper pt-4">
      <h1 class="d-flex justify-content-center">Posts</h1>
      <ul>
        <li v-for="post of posts" :key="post.id" class="mb-3 posts">
          <h2 class="post-title">{{ post.title }}</h2>
          <p class="text-secondary">{{ post.body }}</p>
          <a class="text-light bg-primary p-2 post-link" href="#" @click.prevent="openPost(post)">Open this post</a>
          <hr>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({$axios}) {
    const posts = await $axios.$get('https://jsonplaceholder.typicode.com/posts/')
    return {posts}
  },
  data: () => ({
    posts: []
  }),
  methods: {
    openPost(post) {
      this.$router.push('/' + post.id)
    }
  }
}
</script>

<style>
ul {
  padding: 0 2rem;
}

li {
  list-style: none;
}

a {
  text-decoration: none;
}

.post-title {
  color: #303030;
}

.post-link {
  transition: background-color .2s;
}

.post-link:hover {
  background-color: #0d92ff !important;
  
}
</style>
