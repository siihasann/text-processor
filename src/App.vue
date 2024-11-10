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
    const articleText = ref(articleContent)

    return {
      articleText,
    }
  },
})
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <!-- Header -->
    <header class="bg-gradient-to-r from-blue-500 to-purple-600 text-white p-6 shadow-lg">
      <h1 class="text-4xl font-extrabold text-center mb-2">Text Processor</h1>
      <p class="text-center text-lg">
        Aplikasi untuk pencarian, penggantian, dan pengurutan kata dalam teks
      </p>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto p-6 flex-grow grid gap-8 lg:grid-cols-2">
      <ArticleDisplay
        :content="articleText"
        class="lg:col-span-2 p-4 bg-white shadow-md rounded-lg"
      />

      <TextSearch :text="articleText" class="p-4 bg-gray-50 shadow-md rounded-lg" />
      <TextReplace
        :text="articleText"
        @update:text="articleText = $event"
        class="p-4 bg-gray-50 shadow-md rounded-lg"
      />
      <TextSort :text="articleText" class="p-4 bg-gray-50 shadow-md rounded-lg" />
    </main>

    <!-- Footer -->
    <Footer class="bg-gray-800 text-white py-4 text-center" />
  </div>
</template>

<style scoped>
/* Custom Style Adjustments */
.header {
  background: linear-gradient(135deg, #667eea, #764ba2);
}
</style>
