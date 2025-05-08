<template>
  <div class="post">
    <h3>{{ post.title }}</h3>
    <p>{{ post.message }}</p>
    <button @click="$emit('edit', post.id)">editar</button>
    <button @click="confirmDelete">eliminar</button>
  </div>
</template>

<script>
export default {
  props: ['post'],
  methods: {
    confirmDelete() {
      if (confirm('¿Estás seguro de que deseas eliminar este post?')) {
        this.$emit('delete', this.post.id);
      }
    }
  }
}
</script>
