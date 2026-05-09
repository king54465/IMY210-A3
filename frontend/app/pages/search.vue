<template>
  <div class="container">
    <NuxtLink to="/" class="back-link">← Back to Home</NuxtLink>
    <h1>Search</h1>

    <input v-model="query" type="text" placeholder="Search by title or author..." />

    <div v-if="results.length === 0 && query">
      <p>No results found.</p>
    </div>

    <div v-for="post in results" :key="post.id" class="post-card">
      <NuxtLink :to="`/posts/${post.documentId}`">
        <h2>{{ post.title }}</h2>
      </NuxtLink>
      <p class="post-meta">By {{ post.author }} | {{ post.category }}</p>
      <p>{{ post.content.substring(0, 150) }}...</p>
    </div>
  </div>
</template>

<script setup>
const query = ref('')

const { data } = await useFetch(
  () => `http://localhost:1337/api/posts?filters[$or][0][title][$containsi]=${query.value}&filters[$or][1][author][$containsi]=${query.value}`,
  { watch: [query] }
)

const results = computed(() => data.value?.data || [])
</script>