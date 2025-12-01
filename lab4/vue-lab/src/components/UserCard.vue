<script setup lang="ts">
// TypeScript "на льоту" визначає тип пропсів
// Тепер VUE буде очікувати, що 'username' - це ЗАВЖДИ рядок
// а 'isActive' - ЗАВЖДИ булеве значення.
defineProps<{
  username: string,
  isActive: boolean
}>()
</script>

<template>
  <div
    class="border p-4 mt-3 rounded-lg shadow-sm"
    :class="isActive
        ? 'border-green-500 bg-green-50'
        : 'border-gray-300 bg-white'"
  >
    <h3 class="font-semibold text-lg">{{ username }}</h3>

    <p
      class="text-sm"
      :class="isActive ? 'text-green-700' : 'text-gray-500'"
    >
      Статус: {{ isActive ? 'Онлайн' : 'Офлайн' }}
    </p>
  </div>
</template>

