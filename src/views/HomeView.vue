<template>
  <div class="home">
    <div v-for="post in posts" :key="post.id">
      <APost :post="post"></APost>
    </div>
  </div>
</template>

<script>
import APost from '@/components/APost.vue'

export default {
  name: 'HomeView',
  components: {
    APost
  },

  data () {
    return {
      posts: [],
      error: null
    }
  },

  async created () {
    const url = 'https://jsonplaceholder.typicode.com/posts'

    await fetch(url)
      .then(response => response.json())
      .then(json => {
        this.posts = json
      }).catch(error => {
        console.log(error)
        this.error = error
      })
  }
}
</script>
