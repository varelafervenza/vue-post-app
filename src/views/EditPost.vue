<template>
    <div>
      <h1>Editar Post</h1>
      <PostForm v-if="post" :initialData="post" :isEdit="true" @submit="updatePost" />
    </div>
  </template>
  
  <script>
  import PostForm from '../components/PostForm.vue'
  
  export default {
    components: { PostForm },
    data() {
      return {
        post: null
      }
    },
    created() {
      const id = parseInt(this.$route.params.id)
      const posts = JSON.parse(localStorage.getItem('posts') || '[]')
      console.log('Posts cargados desde localStorage:', posts)
      this.post = posts.find(p => p.id === id)
    },
    methods: {
      updatePost(updatedPost) {
        let posts = JSON.parse(localStorage.getItem('posts') || '[]')
        console.log('Posts cargados desde localStorage:', posts)
        posts = posts.map(p => (p.id === updatedPost.id ? updatedPost : p))
        localStorage.setItem('posts', JSON.stringify(posts))
        this.$router.push('/')
      }
    }
  }
  </script>
  