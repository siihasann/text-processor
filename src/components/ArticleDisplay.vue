<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ArticleDisplay',
  props: {
    content: {
      type: String,
      required: true,
    },
  },
})
</script>

<template>
  <div class="border rounded-lg p-4 bg-green-50 mb-4 overflow-x-auto max-w-full sm:p-6 lg:p-8">
    <pre class="whitespace-pre-wrap break-words text-sm sm:text-base">{{ content }}</pre>
  </div>
</template>

<style scoped>
/* Untuk menghindari scroll horizontal pada artikel */
pre {
  word-wrap: break-word; /* Membungkus kata yang panjang */
  overflow-x: hidden; /* Menghilangkan scroll horizontal */
  max-width: 100%; /* Memastikan teks tidak melampaui lebar kontainer */
}
</style>
