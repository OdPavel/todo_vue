<template>
  <div class=" col-4 card me-3 mb-3">
    <div class="card-header">
      Todo #{{ index + 1 }}
    </div>
    <div class="card-body">
      <h5 class="card-title">{{ title }}</h5>
      <p class="card-text">{{ body }}</p>
      <button
          class="btn btn-danger"
          @click="onDelete(id)"
      >
        Delete
      </button>
    </div>
  </div>

</template>

<script>
export default {
  props: ['title', 'id', 'body', 'index'],
  name: "ListItem",

  methods: {
    onDelete(id) {
      this.$emit('on-delete', id)

    }
  }
}


</script>

<style scoped>
.card {
  max-width: 300px;
  border: 1px solid gray;
  border-radius: 5px;
  background-color: beige;
}
</style>
