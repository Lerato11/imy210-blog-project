<template>
    <div>
        <NuxtLink :to="`blogs/${product.id}`">
            <h2> {{product.title}} </h2>
            <h3> {{product.price}} </h3> <!--author-->
            <p> {{product.description}} </p> <!--snippet ****** -->
        </NuxtLink>
    </div>
</template>

<script setup>
    const {product} = defineProps(['product'])
</script>

<style scoped>

</style>