<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'TextSort',
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    const sortedWords = ref<string[]>([])

    const sortWords = () => {
      // Bersihkan teks dari tanda baca dan ubah ke lowercase
      const cleanText = props.text.toLowerCase().replace(/[.,\/#!$%\^&\*;:{}=\-_`~()]/g, '')

      // Pisah kata dan hapus duplikat
      const uniqueWords = [...new Set(cleanText.split(/\s+/))]

      // Urutkan kata
      sortedWords.value = uniqueWords.sort()
    }

    return {
      sortedWords,
      sortWords,
    }
  },
})
</script>

<template>
  <div class="mb-6">
    <h2 class="text-xl font-semibold mb-2">Pengurutan Kata</h2>
    <button
      @click="sortWords"
      class="bg-purple-500 text-white px-4 py-2 rounded hover:bg-purple-600 mb-2"
    >
      Urutkan Kata
    </button>
    <div v-if="sortedWords.length" class="border rounded p-4 bg-gray-50">
      <div class="grid grid-cols-2 md:grid-cols-4 gap-2">
        <div
          v-for="(word, index) in sortedWords"
          :key="index"
          class="text-sm p-1 border rounded bg-white"
        >
          {{ word }}
        </div>
      </div>
    </div>
  </div>
</template>
