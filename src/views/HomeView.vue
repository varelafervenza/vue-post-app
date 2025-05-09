<template>
  <div>
    <h1>Lista de Posts</h1>
    <button @click="$router.push('/create')">Crear</button>
    <PostList
      :posts="posts"
      @edit="editPost"
      @delete="deletePost"
    />
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'

export default {
  components: { PostList },
  data() {
  const raw = JSON.parse(localStorage.getItem('posts') || '[]')
  // método 2: usando un Set para ids
  const seen = new Set()
  const unique = raw.filter(post => {
    if (seen.has(post.id)) return false
    seen.add(post.id)
    return true
  })
  return { posts: unique }
},
  methods: {
    editPost(id) {
      this.$router.push(`/edit/${id}`)
    },
    deletePost(id) {
      this.posts = this.posts.filter(p => p.id !== id)
      localStorage.setItem('posts', JSON.stringify(this.posts))
    }
  }
}
</script>
