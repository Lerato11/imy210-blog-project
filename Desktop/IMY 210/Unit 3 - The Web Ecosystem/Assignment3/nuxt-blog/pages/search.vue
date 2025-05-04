<template>
    <div>
        <h1>Search Blog Posts</h1>
        <input placeholder="Search by title or author" />
        <br>
        <br>

        <div >
          <div v-for="p in products">
            <!-- <NuxtLink :to="`/blogs/${p.id}`">{{p.title}}</NuxtLink> -->
             <BlogPost :product = "p" />
             <br>
             <hr>
             <br>

          </div>

        </div>

    </div>
</template>

<script setup>
    const { data: products} = await useFetch('https://fakestoreapi.com/products')
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