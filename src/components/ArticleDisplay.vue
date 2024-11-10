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
  <div class="border rounded-lg p-4 bg-green-50 mb-4">
    <pre class="whitespace-pre-wrap">{{ content }}</pre>
  </div>
</template>
