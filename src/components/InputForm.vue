<template>
  <div class="wrapper">
    <form @submit.prevent="onInput" class="form-group">
      <label class="form-label mb-2">Enter your task</label>
      <input
          type="text"
          class="form-control mb-3"
          placeholder="Title"
          v-model="onTask.title"
      >
      <input
          type="text"
          class="form-control mb-3"
          placeholder="body"
          v-model="onTask.body"
      >
      <button class="btn btn-primary">Submit</button>
      <hr>

    </form>
  </div>
</template>

<script>
import {v4 as uuidv4} from 'uuid';

export default {

  data() {
    return {
      onTask: {
        title: '',
        body: ''
      }
    }

  },
  methods: {
    onInput() {
      if (this.onTask.title.trim() !== '' && this.onTask.body.trim() !== '') {
        this.$emit('on-submit', {
          id: uuidv4(),
          title: this.onTask.title,
          body: this.onTask.body

        })
      }
      this.onTask.title = ''
      this.onTask.body = ''
    },

  }
}
</script>


<style scoped>
.wrapper {
  max-width: 600px;
  margin: 50px auto;
}
</style>
