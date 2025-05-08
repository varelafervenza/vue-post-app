<template>
    <div>
      <PostItem
        v-for="post in posts"
        :key="post.id"
        :post="post"
        @edit="$emit('edit', $event)"
        @delete="$emit('delete', $event)"
      />
    </div>
  </template>
  
  <script>
  import PostItem from './PostItem.vue'
  
  export default {
    props: {
      posts: {
        type: Array,
        required: true
      }
    },
    components: { PostItem }
  }
  </script>
  