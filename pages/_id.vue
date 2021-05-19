<template>
  <div class="container">
    <h2 class="d-flex justify-content-center">{{ post.title }}</h2>
    <p>{{ post.body }}</p>
    <nuxt-link class="text-light bg-primary p-2 post-link" :to="`/${post.id}/comments`">View comments</nuxt-link>
    <nuxt />
  </div>
</template>

<script>
export default {
  validate({params}) {
    return /^\d+$/.test(params.id)
  },
  async asyncData({$axios, params}) {
    const post = await $axios.$get('https://jsonplaceholder.typicode.com/posts/' + params.id)
    return {post}
  },
  data: () => ({
    post: []
  })
}
</script>