<script lang="ts">
import { defineComponent, ref } from 'vue'
import ArticleDisplay from './components/ArticleDisplay.vue'
import TextSearch from './components/TextSearch.vue'
import TextReplace from './components/TextReplace.vue'
import TextSort from './components/TextSort.vue'
import articleContent from './utils/articleData'
import Footer from './components/Footer.vue'

export default defineComponent({
  name: 'App',
  components: {
    ArticleDisplay,
    TextSearch,
    TextReplace,
    TextSort,
    Footer,
  },
  setup() {
    const articleText = ref(articleContent) // Masukkan teks artikel lengkap di sini

    return {
      articleText,
    }
  },
})
</script>

<template>
  <div class="container mx-auto p-4">
    <h1 class="text-3xl font-bold mb-6">Text Processor</h1>

    <ArticleDisplay :content="articleText" />
    <TextSearch :text="articleText" />
    <TextReplace :text="articleText" @update:text="articleText = $event" />
    <TextSort :text="articleText" class="mb-80" />
  </div>
  <Footer class="mt-10" />
</template>
