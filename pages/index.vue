<template>
  <div class="max-w-screen-md mx-auto prose px-8">
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
    <div class="max-w-xs mt-4 mx-auto">
      <ul class="p-0">
        <li
          v-for="post in posts"
          :key="post.title"
          class="list-none my-4 p-0"
        >
          <p class="flex flex-col m-0">
            <span class="text-xs">
              {{ post['publish-date'] | formatDate }}
            </span>
            <a
              :href="`/${post.slug}`"
            >
              {{ post.title }}{{ post.subtitle ? `: ` + post.subtitle : "" }}
            </a>
          </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  filters: {
    formatDate: (dateString) => {
      const date = new Date(dateString)
      const options = {
        year: 'numeric',
        month: 'long',
        day: '2-digit'
      }
      return date.toLocaleString('en-US', options)
    }
  },
  async asyncData ({ $content }) {
    const posts = await $content()
      .where({
        'publish-date': {
          $ne: false
        }
      })
      .only(['publish-date', 'slug', 'title', 'subtitle'])
      .sortBy('publish-date', 'desc')
      .fetch()
    return {
      posts
    }
  }
}
</script>
