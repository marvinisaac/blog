<template>
  <article class="max-w-screen-md mx-auto prose px-8">
    <NuxtLink
      to="/"
      href="/"
      class="block my-4 text-gray-400 text-right"
    >
      ← Go Back
    </NuxtLink>
    <div class="border-b border-t py-8">
      <h1 class="my-0 text-center">
        {{ post.title }}
      </h1>
      <h3 class="my-0 text-center">
        {{ post.subtitle }}
      </h3>
    </div>
    <p class="text-gray-400 text-right text-xs">
      {{ post['publish-date'] | formatDate }}
    </p>
    <nuxt-content class="mt-4" :document="post" />
    <NuxtLink
      to="/"
      href="/"
      class="block mb-16 mt-4 text-gray-400 text-right"
    >
      ← Go Back
    </NuxtLink>
  </article>
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
  async asyncData ({ $content, params }) {
    const post = await $content(params.slug).fetch()
    return { post }
  },
  head () {
    const post = this.post
    const subtitle = post.subtitle ? `: ${post.subtitle}` : ''
    return {
      title: `${post.title}${subtitle} | Marvin's Blog`,
      meta: [{
        hid: 'description',
        name: 'description',
        content: post.blurb || 'Marvin\'s Blog'
      }]
    }
  }
}
</script>
