<template>
  <div class="comments-block">
    <h4 class="comments-title">Comments</h4>
    <div class="comments" v-for="comment of comments" :key="comment.id">
      <h5 >{{ comment.email }}</h5>
      <p>{{ comment.body }}</p>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({$axios, params}) {
    const comments = await $axios.$get('https://jsonplaceholder.typicode.com/posts/' + params.id + '/comments')
    return {comments}
  },
  data: () => ({
    comments: []
  })
}
</script>

<style>
.comments-title {
  margin: 20px 0 20px;
}

.comments {
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 10px;
}
</style>