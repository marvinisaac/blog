<template>
  <article class="mx-auto max-w-screen-md">
    <div>
      <NuxtLink to="/" href="/" class="block text-gray-400 mt-8">
        ← Go Back
      </NuxtLink>
      <h1 class="text-5xl font-black mt-2">
        {{ post.title }}
      </h1>
    </div>
    <nuxt-content class="mt-4 prose max-w-full" :document="post" />
  </article>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const post = await $content(params.slug).fetch()
    return { post }
  }
}
</script>
