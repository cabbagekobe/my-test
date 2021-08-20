<template>
  <div>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <h1>
          <NuxtLink :to="`/posts/${post.id}`">
            title: {{ post.title }}
          </NuxtLink>
        </h1>

        <p>
          id: {{ post.id }}
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        posts: []
      }
    },

    async asyncData({ app }) {
      const baseUrl = 'https://jsonplaceholder.typicode.com/posts'
      const response = await app.$axios.$get(baseUrl)

      return {
        posts: response
      }
    }
  }
</script>
