<template>
    <div>
      <h1>Crear Post</h1>
      <PostForm @submit="createPost" />
    </div>
  </template>
  
  <script>
  import PostForm from '../components/PostForm.vue'
  
  export default {
    components: { PostForm },
    methods: {
      createPost(post) {
        const posts = JSON.parse(localStorage.getItem('posts') || '[]')
        console.log('Posts cargados desde localStorage:', posts)
        post.id = Date.now()
        posts.push(post)
        localStorage.setItem('posts', JSON.stringify(posts))
        this.$router.push('/')
      }
    }
  }
  </script>
  