<template>
    <div class="max-w-3xl mx-auto p-6">
        <h1 class="text-3xl font-bold mb-6 text-center" >Search Blog Posts</h1>

        <input type="text" id="search" v-model="search" placeholder="e.g. Mike or Roadmap"
            class="p-2 border border-gray-300 rounded w-full"
        />

        <br>
        <br>

        <div v-if="pending">Loading...</div>
        <div v-else-if="error">Error loading blog posts.</div>

        <div class="space-y-6" v-else>
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
    // const { data: products} = await useFetch('https://fakestoreapi.com/products')

    const { data: response, pending, error } = await useFetch('http://localhost:1337/api/blogs');
  // const { data: products} = await useFetch('https://fakestoreapi.com/products')

  const blogs = computed(() => response.value?.data  || []);


  const search = ref("");

  const filteredBlogs = computed(() => {


    if (search.value.trim()) {
        const searched = search.value.trim().toLowerCase();


        return blogs.value.filter(blog =>
                blog.title.toLowerCase().includes(searched) || blog.author.toLowerCase().includes(searched) );
    }

    // if emty
    return blogs.value; 

    // return blogs.value.filter(blog => blog.category === selectedCategory.value);

    

    });
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