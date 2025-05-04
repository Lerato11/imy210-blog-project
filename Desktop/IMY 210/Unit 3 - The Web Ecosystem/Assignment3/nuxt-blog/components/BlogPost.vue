<template>
    <div>
        <NuxtLink :to="`blogs/${blogPost.documentId}`" class="block p-6 rounded-lg shadow hover:shadow-md transition bg-white">
            <h2 class="text-xl font-semibold mb-2 text-gray-800"> {{blogPost.title}} </h2>
            <h3 class="text-sm text-gray-500 mb-1"> {{blogPost.author}} </h3> <!--author-->
            <p class="text-gray-600 text-sm"> {{blogPost.snippet}} </p> <!--snippet ****** -->
        </NuxtLink>
    </div>
</template>

<script setup>
    const {blogPost} = defineProps(['blogPost'])
    // const {product} = defineProps(['product'])

</script>

<style scoped>

</style>
