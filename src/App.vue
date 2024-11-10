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
  <div class="min-h-screen flex flex-col overflow-hidden">
    <!-- Header -->
    <header class="bg-gradient-to-r from-blue-500 to-purple-600 text-white p-4 md:p-6 shadow-lg">
      <h1 class="text-3xl md:text-4xl font-extrabold text-center mb-1 md:mb-2">Text Processor</h1>
      <p class="text-center text-sm md:text-lg">
        Aplikasi untuk pencarian, penggantian, dan pengurutan kata dalam teks
      </p>
    </header>

    <!-- Main Content -->
    <main class="container mx-auto p-4 md:p-6 flex-grow grid gap-4 grid-cols-1 lg:grid-cols-2">
      <!-- Article Display Component -->
      <section
        class="lg:col-span-2 bg-white shadow-md rounded-lg p-4 overflow-y-auto max-h-[30vh] md:max-h-[40vh]"
      >
        <ArticleDisplay :content="articleText" />
      </section>

      <!-- Text Processor Components -->
      <section class="p-4 bg-gray-50 shadow-md rounded-lg w-full">
        <TextSearch :text="articleText" />
      </section>
      <section class="p-4 bg-gray-50 shadow-md rounded-lg w-full md:w-auto">
        <TextReplace :text="articleText" @update:text="articleText = $event" />
      </section>
      <section class="p-4 bg-gray-50 shadow-md rounded-lg w-full md:w-auto">
        <TextSort :text="articleText" />
      </section>
    </main>

    <!-- Footer -->
    <Footer class="bg-gray-800 text-white py-4 text-center mt-4 w-full" />
  </div>
</template>

<style scoped>
/* Menghapus scroll horizontal */
body {
  overflow-x: hidden;
}
</style>
