<template>
    <form @submit.prevent="handleSubmit">
      <input v-model="post.title" placeholder="Título" required />
      <textarea v-model="post.message" placeholder="Mensaje" required></textarea>
      <button type="submit">{{ isEdit ? 'Actualizar' : 'Crear' }}</button>
    </form>
  </template>
  
  <script>
  export default {
    props: {
      initialData: {
        type: Object,
        default: () => ({ title: '', message: '', id: null })
      },
      isEdit: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        post: { ...this.initialData }
      }
    },
    methods: {
      handleSubmit() {
        const { id, title, message } = this.post
        this.$emit('submit', { id, title, message }) // <-- solo los datos planos
      }
    }
  }
  </script>
  