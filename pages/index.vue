<template>
  <div class="max-w-screen-md mx-auto prose">
    <a
      href="https://marvinisaac.com"
      class="block my-4 text-gray-400 text-right"
    >
      ← Go Home
    </a>
    <div class="border-b border-t">
      <h1 class="my-8 text-center">
        Marvin's Blog
      </h1>
    </div>
    <div class="mt-4">
      <ul>
        <li
          v-for="post in posts"
          :key="post.title"
        >
          <a
            :href="`/${post.slug}`"
          >
            {{ post.title }}
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const posts = await $content()
      .where({
        'publish-date': {
          $ne: false
        }
      })
      .only(['publish-date', 'slug', 'title'])
      .sortBy('publish-date', 'desc')
      .fetch()
    return {
      posts
    }
  }
}
</script>
