<template>
  <div>
    <h1>
      {{ post.title }}
    </h1>

    <p>
      {{ post.body }}
    </p>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    data() {
      return {
        post: []
      }
    },

    async asyncData({ params }) {
      const { data } = await axios.get(
        `https://jsonplaceholder.typicode.com/posts/${params.slug}`
      )

      return {
        post: data
      }
    }
  }
</script>
