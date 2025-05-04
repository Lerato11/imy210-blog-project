<template>
    <div>
            <h2> {{product.title}} </h2>
            <h3> {{product.price}} </h3> <!--author-->
            <p> {{product.description}} </p> <!--description ******-->
            <p> {{product.id}} </p>
            <p> ----------------------------------- </p>

        
    </div>
</template>

<script setup>
    const {product} = defineProps(['product'])
</script>

<style scoped>

</style>