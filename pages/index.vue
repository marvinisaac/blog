<template>
  <div class="mx-auto prose max-w-screen-md">
    <h1 class="text-7xl font-black text-center">
      Marvin's Posts
    </h1>
    <ul class="grid grid-cols-3 gap-8 mt-8">
      <a
        v-for="post in posts"
        :key="post.title"
        :href="`/${post.slug}`"
      >
        {{ post.title }}
      </a>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const posts = await $content()
      .only(['title', 'slug'])
      .sortBy('createdAt', 'desc')
      .fetch()
    return {
      posts
    }
  }
}
</script>
