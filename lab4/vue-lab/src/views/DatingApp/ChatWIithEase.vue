<script setup lang="ts">
const emit = defineEmits(['next', 'skip']);
</script>

<template>
  <div class="flex flex-col justify-between items-center w-full max-w-[360px] mx-auto min-h-[calc(100vh-150px)]">

    <div class="flex flex-col items-center w-full">

      <div class="w-full flex justify-center mt-2 mb-[40px]">
        <img
          src="/images/couple.png"
          alt="Chat with ease"
          class="w-[280px] object-contain"
        />
      </div>

      <h2
        class="bg-[#FF5F5F] text-white text-[16px] font-bold tracking-wide
             py-3 rounded shadow-sm text-center uppercase w-[80%]"
      >
        CHAT WITH EASE
      </h2>

      <p
        class="text-gray-500 text-[13px] text-center
               leading-relaxed tracking-wide mt-[45px] mb-4"
      >
        Maecenas in placerat nibh. Integer sollicitudin sapien et massa varius venenatis.
        Nulla facilisis purus nec nibh posuere volutpat.
      </p>
    </div>

    <div class="w-full flex justify-between items-center pb-4">
      <button
        @click="$emit('skip')"
        class="min-w-[80px] h-[45px] text-[13px] font-semibold tracking-wider uppercase
             bg-[#F5F5FF] text-[#5A5A64] rounded transition-all duration-300
             hover:bg-white hover:shadow-lg hover:shadow-gray-300"
      >
        Skip
      </button>

      <div class="flex gap-3">
        <span class="w-2.5 h-2.5 bg-[#FF5F5F] rounded-full"></span>
        <span class="w-2.5 h-2.5 bg-gray-200 rounded-full"></span>
        <span class="w-2.5 h-2.5 bg-gray-200 rounded-full"></span>
      </div>

      <button
        @click="$emit('next')"
        class="min-w-[80px] h-[45px] text-[13px] font-semibold tracking-wider uppercase
             bg-[#FF5F5F] text-white rounded shadow-md transition-all duration-300
             hover:bg-[#ff4444] hover:shadow-lg hover:shadow-[#FF5F5F]/50"
      >
        Next
      </button>
    </div>

  </div>
</template>

<style scoped></style>
