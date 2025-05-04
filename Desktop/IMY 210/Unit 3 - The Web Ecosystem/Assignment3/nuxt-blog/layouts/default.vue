<template>
    <div>

        <header class="shadow-sm bg-gray-950 border-b border-gray-800" >
            <nav class="container mx-auto p-4 flex justify-between text-gray-100">
                <NuxtLink to="/">Blogs</NuxtLink>
                <ul class="flex gap-4">
                    <li><NuxtLink to="/">Home</NuxtLink></li>
                    <li><NuxtLink to="/search">Search</NuxtLink></li>
                    <!-- <li><NuxtLink to="/blogs">Products</NuxtLink></li> delete this -->
                </ul>
            </nav>
        </header>

        <div class="container mx-auto p-4">
            <slot />
        </div>

    </div>
</template>


<style scoped>
    .router-link-exact-active {
        color: #12b488;
    }
</style>