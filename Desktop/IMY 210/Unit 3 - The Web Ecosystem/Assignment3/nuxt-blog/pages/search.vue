<template>
    <div class="max-w-3xl mx-auto p-6">
        <h1 class="text-3xl font-bold mb-6 text-center" >Search Blog Posts</h1>
        <input placeholder="Search by title or author" 
            class="w-full border border-gray-300 rounded-md p-2 mb-6 focus:outline-none focus:ring-2 focus:ring-blue-400" />
        <br>
        <br>

        <div v-if="pending">Loading...</div>
      <div v-else-if="error">Error loading blog posts.</div>

        <div class="space-y-6" v-else>
          <div v-for="blog in blogs" :key="blog.documentId" class="mb-6">
            <!-- <NuxtLink :to="`/blogs/${p.id}`">{{p.title}}</NuxtLink> -->
            <BlogPost :blogPost="{
                documentId: blog.documentId,
                title: blog.title,
                author: blog.author,
                description: blog.snippet
              }" />
             <br>
             <hr>
             <br>

          </div>

        </div>

    </div>
</template>

<script setup>
    // const { data: products} = await useFetch('https://fakestoreapi.com/products')

    const { data: response, pending, error } = await useFetch('http://localhost:1337/api/blogs');
  // const { data: products} = await useFetch('https://fakestoreapi.com/products')

  const blogs = computed(() => response.value?.data || []);
</script>

<style scoped>
    h2{
        margin-bottom: 20px;
        font-size: 36px;
    }

    p{
        margin: 20px 0;
    }
</style>