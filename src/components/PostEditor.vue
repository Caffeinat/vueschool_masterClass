<template>
  <div class="col-full">
    <form @submit.prevent="save">
      <div class="form-group">
        <label for="thread_title">Title:</label>
        <input type="text" id="thread_title" class="form-input" name="title" />
      </div>

      <div class="form-group">
        <label for="thread_content">Content:</label>
        <textarea
          v-model="text"
          id="thread_content"
          class="form-input"
          name="content"
          rows="8"
          cols="140"
        ></textarea>
      </div>
      <div class="btn-group">
        <button class="btn btn-ghost">Cancel</button>
        <button class="btn btn-blue" type="submit" name="Publish">Publish</button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const text = ref('')
// emit events
const emit = defineEmits(['save'])

// Methods
const save = () => {
  const postId = 'gggg' + Math.random()
  const post = {
    id: postId,
    text: text.value,
    publishedAt: Math.floor(Date.now() / 1000),
    userId: 'ALXhxjwgY9PinwNGHpfai6OWyDu2'
  }
  emit('save', { post })
  // props.posts.push(post)
  // thread.value.posts.push(postId)
  text.value = ''
}
</script>
