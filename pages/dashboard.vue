<template>
  <div>
    <b-table :items="posts" :fields="fields"> </b-table>
  </div>
</template>

<script>
import Vue from 'vue'
export default Vue.extend({
  middleware: ['auth'],
  data() {
    return {
      fields: ['userId', 'title', 'body'],
      posts: [],
    }
  },
  async beforeMount() {
    this.$axios
      .$get('https://jsonplaceholder.typicode.com/posts')
      .then((res) => {
        this.posts = res
      })
      .catch((err) => {
        console.log(err)
      })
  },
})
</script>