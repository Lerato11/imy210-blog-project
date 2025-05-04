<template>
    <div class="max-w-3xl mx-auto p-6 bg-white rounded-lg shadow">
            <h2 class="text-3xl font-bold mb-4 text-gray-800"> {{blogPost.title}} </h2>
            <h3 class="text-sm text-gray-500 mb-6"> By: {{blogPost.price}} </h3> <!--author-->

            <div class="text-gray-700 leading-relaxed text-base space-y-4"> <!--content-->
                
                <p v-for="(block, index) in blogPost.content" :key="index">
                
                    {{ block.children[0]?.text }}
                </p>
            </div>
            
            <!-- <p> {{product.id}} </p>
            <p> ----------------------------------- </p> -->

        
    </div>
</template>

<script setup>
    // const {product} = defineProps(['product'])
    const {blogPost} = defineProps(['blogPost'])

</script>

<style scoped>

</style>