// src/components/Footer.vue
<template>
  <footer class="bg-gray-800 text-white py-4 text-center">
    <p class="text-sm">
      &copy; {{ new Date().getFullYear() }}. Project ini dibuat oleh Hasan Najib.
    </p>
  </footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Footer',
})
</script>

<style scoped>
footer {
  position: fixed;
  bottom: 0;
  width: 100%;
}
</style>
