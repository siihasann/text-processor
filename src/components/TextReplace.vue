<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'TextReplace',
  props: {
    text: {
      type: String,
      required: true,
    },
  },
  emits: ['update:text'],
  setup(props, { emit }) {
    const findTerm = ref('')
    const replaceTerm = ref('')

    const replaceText = () => {
      if (!findTerm.value || !replaceTerm.value) return
      const regex = new RegExp(findTerm.value, 'gi')
      const newText = props.text.replace(regex, replaceTerm.value)
      emit('update:text', newText)
    }

    return {
      findTerm,
      replaceTerm,
      replaceText,
    }
  },
})
</script>

<template>
  <div class="mb-6">
    <h2 class="text-xl font-semibold mb-2">Penggantian Kata</h2>
    <div class="flex gap-4 mb-2">
      <input
        v-model="findTerm"
        type="text"
        placeholder="Kata yang akan diganti"
        class="border rounded px-3 py-2 flex-1"
      />
      <input
        v-model="replaceTerm"
        type="text"
        placeholder="Diganti dengan"
        class="border rounded px-3 py-2 flex-1"
      />
      <button
        @click="replaceText"
        class="bg-green-500 text-white px-4 py-2 rounded hover:bg-green-600"
      >
        Ganti
      </button>
    </div>
  </div>
</template>
