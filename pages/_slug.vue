<template>
  <article class="max-w-screen-md mx-auto prose">
    <NuxtLink
      to="/"
      href="/"
      class="block my-4 text-gray-400 text-right"
    >
      ← Go Back
    </NuxtLink>
    <div class="border-b border-t">
      <h1 class="my-8 text-center">
        {{ post.title }}
      </h1>
    </div>
    <nuxt-content class="mt-4" :document="post" />
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
