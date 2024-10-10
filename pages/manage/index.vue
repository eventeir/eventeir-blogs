<template>
  <div class="container mx-auto p-4">
    <h1 class="h3 font-bold mb-4 text-white">Manage Blogs</h1>
    <table class="min-w-full bg-white border border-gray-300">
      <thead>
        <tr class="bg-gray-200">
          <th class="py-2 px-4 border-b">Title</th>
          <th class="py-2 px-4 border-b">Publish</th>
          <th class="py-2 px-4 border-b">Status</th>
          <th class="py-2 px-4 border-b">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(blog, index) in blogs" :key="index" class="text-center">
          <td class="py-2 px-4 border-b">{{ blog.title }}</td>
          <td class="py-2 px-4 border-b">
            <label class="switch">
              <input
                type="checkbox"
                :checked="blog.is_published"
                @change="togglePublish(blog.blog_id)"
              />
              <span class="slider"></span>
            </label>
          </td>
          <td class="py-2 px-4 border-b">{{ blog.status }}</td>
          <td class="py-2 px-4 border-b">
            <NuxtLink :to="`/edit/${blog.blog_id}`" class="text-blue-500">Edit</NuxtLink>
            <button @click="deleteBlog(blog.blog_id)" class="text-red-500 ml-2">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
const blogs = ref([
  { blog_id: '1', title: 'First Blog', is_published: false, status: 'draft' },
  { blog_id: '2', title: 'Second Blog', is_published: true, status: 'published' },
]);

const togglePublish = (id: string) => {
  const blog = blogs.value.find(b => b.blog_id === id);
  if (blog) {
    blog.is_published = !blog.is_published;
    console.log(`Toggled publish status for blog with ID: ${id}. New status: ${blog.is_published}`);
  }
};

const deleteBlog = (id: string) => {
  console.log(`Deleted blog with ID: ${id}`);
};
</script>

<style scoped>
.switch {
  position: relative;
  display: inline-block;
  width: 48px;
  height: 24px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  transition: 0.4s;
  border-radius: 34px;
}

.slider:before {
  position: absolute;
  content: '';
  height: 18px;
  width: 18px;
  border-radius: 50%;
  left: 4px;
  bottom: 3px;
  background-color: white;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: theme('colors.primary.300');
}

input:checked + .slider:before {
  transform: translateX(24px);
}
</style>
