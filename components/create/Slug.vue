<template>
  <ui-card-wrapper class="bg-primary-100 text-white">
    <div
      class="cursor-pointer flex justify-between items-center p-4 border-b border-gray-300 bg-primary-100 text-gray-100"
      @click="toggleSlug"
    >
      <div class="text-lg font-semibold">Slug</div>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        :class="isExpanded ? 'rotate-180 transition-transform duration-300' : 'transition-transform duration-300'"
        class="h-5 w-5 text-gray-300"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
        stroke-width="2"
      >
        <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
      </svg>
    </div>

    <div
      :class="isExpanded ? 'max-h-[200px] opacity-100' : 'max-h-0 opacity-0'"
      class="transition-all py-4 duration-300 overflow-hidden text-gray-100"
    >
      <div class="flex flex-col">
        <label class="text-small font-bold mb-2" for="slug">Slug</label>
        <input
          class="border-2 border-primary-200 py-2 px-4 rounded-md text-primary-200"
          type="text"
          id="slug"
          v-model="slug"
          placeholder="slug"
        />
      </div>
    </div>
  </ui-card-wrapper>
</template>

<script setup lang="ts">

// Reactive variable to control visibility
const isExpanded = ref(false);
const slug = ref('');
// Toggle function for Slug section
const toggleSlug = () => {
  isExpanded.value = !isExpanded.value;
};
</script>
