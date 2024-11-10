<script lang="ts">
import { defineComponent, ref, watch } from 'vue'

export default defineComponent({
  name: 'TextSearch',
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    const searchTerm = ref('')
    const searchCount = ref(0)

    const searchWord = () => {
      if (!searchTerm.value) {
        searchCount.value = 0
        return
      }
      const regex = new RegExp(searchTerm.value, 'gi')
      const matches = props.text.match(regex)
      searchCount.value = matches ? matches.length : 0
    }

    // Watch searchTerm and update searchCount every time searchTerm changes
    watch(searchTerm, searchWord)

    return {
      searchTerm,
      searchCount,
      searchWord,
    }
  },
})
</script>

<template>
  <div class="mb-6">
    <h2 class="text-xl font-semibold mb-2">Pencarian Kata</h2>
    <div class="flex gap-4">
      <input
        v-model="searchTerm"
        type="text"
        placeholder="Masukkan kata yang dicari"
        class="border rounded px-3 py-2 flex-1"
      />
      <button
        @click="searchWord"
        class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
      >
        Cari
      </button>
    </div>
    <p v-if="searchCount > 0" class="mt-2 text-green-600">
      Kata "{{ searchTerm }}" ditemukan {{ searchCount }} kali
    </p>
    <p v-else-if="searchTerm && searchCount === 0" class="mt-2 text-red-600">
      Kata "{{ searchTerm }}" tidak ditemukan
    </p>
  </div>
</template>
