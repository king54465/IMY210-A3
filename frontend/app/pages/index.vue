<template>
  <div class="container">
    <h1>My Blog</h1>

    <select v-model="selectedCategory">
      <option value="">All Categories</option>
      <option v-for="cat in categories" :key="cat" :value="cat">{{ cat }}</option>
    </select>

    <div v-for="post in filteredPosts" :key="post.id" class="post-card">
      <NuxtLink :to="`/posts/${post.documentId}`">
        <h2>{{ post.title }}</h2>
      </NuxtLink>
      <p class="post-meta">By {{ post.author }} | {{ post.category }}</p>
      <p>{{ post.content.substring(0, 150) }}...</p>
    </div>
  </div>
</template>

<script setup>
const { data } = await useFetch('http://localhost:1337/api/posts')
const posts = computed(() => data.value?.data || [])

const selectedCategory = ref('')

const categories = computed(() => {
  return [...new Set(posts.value.map(p => p.category))]
})

const filteredPosts = computed(() => {
  if (!selectedCategory.value) return posts.value
  return posts.value.filter(p => p.category === selectedCategory.value)
})
</script>