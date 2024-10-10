<template>
  <ui-card-wrapper class="bg-primary-100 text-white">
    <div class="flex flex-col">
      <label class="text-small font-bold mb-2" for="title">Title</label>
      <input
        class="border-2 border-primary-200 py-2 px-4 rounded-md text-primary-200"
        type="text"
        id="title"
        v-model="title"
        placeholder="Title"
      />
    </div>
    <div class="flex flex-col my-2">
      <label class="text-small font-bold mb-2" for="content">Content</label>
      <textarea
        class="border-2 border-primary-200 py-2 px-4 rounded-md min-h-[250px] text-primary-200"
        id="content"
        v-model="content"
        placeholder="Content"
      ></textarea>
    </div>
  </ui-card-wrapper>
</template>
<script setup lang="ts">
const title = ref('');
const content = ref('');
</script>