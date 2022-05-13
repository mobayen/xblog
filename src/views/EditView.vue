<template>
  <div>

    <div v-if="error" class="bg-red-500 text-white/80 p-2 m-2 rounded">
      ERROR: {{ error }}
    </div>

    <header class="my-10">

      <h2 class="text-center text-2xl">
        Edit the post {{ post.id }}
      </h2>

      <nav class="text-right">
        <router-link :to="{ name: 'post', params: { postId: post.id} }" > Back to post</router-link>
      </nav>
    </header>

    <main>
      <div class="bg-gray-300 flex flex-col p-1 m-1">
        <label for="title" class="">Title</label>
        <input
          type="text"
          id="title"
          :value="post.body"
          class="bg-white/50 p-2 m-1 rounded text-lg"
        >
      </div>
      <div class="bg-gray-300 flex flex-col p-1 m-1">
        <label for="title">Body</label>
        <textarea
          id="title"
          :value="post.body"
          class="bg-white/50 p-2 m-1 rounded text-lg"
        />
      </div>

      <div class="text-center p-2 m-2">
        <button
          class="bg-blue-500 bg-opacity-60 px-4 py-2 rounded text-white hover:bg-opacity-80 m-2"
          @click="updatePost"
        >SUBMIT</button>
      </div>
    </main>

  </div>
</template>

<script>
export default {
  data () {
    return {
      post: {},
      error: 'fake error'
    }
  },

  methods: {
    updatePost () {
      const api = 'https://jsonplaceholder.typicode.com/posts/' + this.$route.params.postId
      const data = {
        title: this.post.title,
        body: this.post.body
      }

      fetch(api, {
        method: 'PUT',
        body: JSON.stringify(data),
        headers: {
          'Content-Type': 'application/json'
        }
      })
        .then(response => response.json())
        .then(json => {
          this.post = json
        }).catch(error => {
          this.error = error.message
        })
    }
  },

  created () {
    console.log(this.$route.params.postId)
    const api = 'https://jsonplaceholder.typicode.com/posts/' + this.$route.params.postId

    fetch(api)
      .then(response => response.json())
      .then(json => {
        this.post = json
      }).catch(error => {
        this.error = error.message
      })
  }
}
</script>
