<template>
  <div class="container">
    <NuxtLink to="/" class="back-link">← Back to Home</NuxtLink>
    <div v-if="post">
      <h1>{{ post.title }}</h1>
      <p class="post-meta">By {{ post.author }} | {{ post.category }}</p>
      <p>{{ post.content }}</p>
    </div>
  </div>
</template>

<script setup>
const route = useRoute()
const { data } = await useFetch(`http://localhost:1337/api/posts?filters[documentId][$eq]=${route.params.id}`)
const post = computed(() => data.value?.data?.[0] || null)
</script>