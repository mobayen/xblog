<template>
  <div class="bg-purple-300/30 rounded p-5 my-4">
    <header class="">
      <router-link :to="{ name: 'post', params: { postId: post.id} }" class="text-2xl ">
        {{ post.title }}
      </router-link>
    </header>
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
