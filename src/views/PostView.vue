<template>
  <div>

    <div v-if="error" class="bg-red-500 text-white/80 p-2 m-2 rounded">
      ERROR: {{ error }}
    </div>

    <header class="my-10">
      <h1 class="text-4xl text-center ">
        {{ post.title }}
      </h1>
      <nav class="text-right">
        <router-link
          :to="{ name: 'edit', params: { postId: post.id} }"
          class="bg-rose-500 px-6 py-2 rounded text-white hover:bg-opacity-80 m-2"
        >
          Edit
        </router-link>
      </nav>
    </header>

    <main>
      <div>
        {{ post.body }}
      </div>
    </main>

  </div>
</template>

<script>
export default {
  data () {
    return {
      post: {}
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
        console.log(error)
        this.error = error.message
      })
  }
}
</script>
