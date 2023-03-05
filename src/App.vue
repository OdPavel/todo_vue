<template>
  <div class="container text-center">
    <input-form
        @on-submit="onInput( $event )"
    >
    </input-form>

    <div class="row align-items-start">
      <list-item
          v-for="(item, index) in arrTasks"
          :title="item.title"
          :body="item.body"
          :id="item.id"
          :index="index"
          :key="item.id"
          @on-delete="deleteItem"
      >
      </list-item>
    </div>
  </div>
</template>

<script>
import InputForm from './components/InputForm'
import ListItem from "@/components/ListItem";

export default {
  components: {
    InputForm,
    ListItem,
  },
  data() {
    return {
      arrTasks: [],
    }
  },
  methods: {

    onInput(data) {
      return this.arrTasks.push(data)
    },

    deleteItem(id) {
      const pos = this.arrTasks.map(e => e.id).indexOf(id);
      this.$delete(this.arrTasks, pos)
      // this.arrTasks.splice(pos, 1)
    }

  },


}
</script>

<style>

</style>
