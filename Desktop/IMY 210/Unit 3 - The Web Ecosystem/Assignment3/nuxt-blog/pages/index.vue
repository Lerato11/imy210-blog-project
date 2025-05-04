<template>
    <div class="max-w-3xl mx-auto p-6">
      <h1 class="text-3xl font-bold mb-6 text-center">All Blog Posts</h1>
      <br>
      <br>

      <div v-if="pending">Loading...</div>
      <div v-else-if="error">Error loading blog posts.</div>

        <div class="space-y-6" v-else>

           <!--category filter -->
          <div class="mb-6">
            <label for="category" class="block text-sm font-medium text-gray-700 mb-2">Filter by Category</label>
            <select v-model="selectedCategory" id="category" class="p-2 border border-gray-300 rounded">
              <option value="">All</option>
              <option value="Law">Law</option>
              <option value="Science">Science</option>
              <option value="Business">Business</option>
              <option value="Travel">Travel</option>
            </select>
          </div>

          <div v-for="blog in filteredBlogs" :key="blog.documentId" class="mb-6">

            <!-- <NuxtLink :to="`/blogs/${p.id}`">{{p.title}}</NuxtLink> -->
              <BlogPost :blogPost="{
                documentId: blog.documentId,
                title: blog.title,
                author: blog.author,
                snippet: blog.snippet
              }" />
             <br>
             <hr>
             <br>

          </div>

        </div>
    </div>
</template>




<script setup>
  const { data: response, pending, error } = await useFetch('http://localhost:1337/api/blogs');
  // const { data: products} = await useFetch('https://fakestoreapi.com/products')

  const blogs = computed(() => response.value?.data || []);

  const selectedCategory = ref("");

  const filteredBlogs = computed(() => {


    if (!selectedCategory.value) {
      return blogs.value;
    }

    return blogs.value.filter(blog => blog.category === selectedCategory.value);
  });


</script>

<style scoped>
    h2{
        margin-bottom: 20px;
        font-size: 36px;
    }

</style>

