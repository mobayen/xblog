<template>
  <div class="bg-purple-300/30 rounded p-5 my-4">
    <!-- <pre class="bg-red-300 p-1 m-1">{{post}}</pre> -->

    <header class="mb-4">
      <router-link to="/#" class="text-2xl ">
        {{ post.title }}
      </router-link>
    </header>

    <main>
      {{ post.body }}
    </main>

  </div>
</template>

<script>
export default {
  name: 'APost',
  props: {
    post: {
      type: Object,
      default: () => ({})
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
