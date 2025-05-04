<template>
    <div>
        <BlogView :blogPost="BlogPost" v-if="BlogPost" />
    </div>
</template>

<script setup>
    const { documentId } = useRoute().params


    // const uri = 'https://fakestoreapi.com/products/' + id;
    const uri = 'http://localhost:1337/api/blogs/' + documentId;

    const {data : response } = await useFetch(uri, {key: documentId});


    const BlogPost = computed(() => {
        const blog = response.value?.data;
        if (!blog) return null;

        //all info
        return {
            id: blog.id,
            documentId: blog.documentId,
            title: blog.title,
            author: blog.author,
            snippet: blog.snippet,
            content: blog.content
        };
    });

</script>

<style  scoped>

</style>


