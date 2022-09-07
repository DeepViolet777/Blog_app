<template>
<div>
    <h3>Последние записи:</h3>
    <post-item 
    :post="post"
    v-for="post in posts" :key="post.id"
     />

</div>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
    components: {
        PostItem
    },
    props: {
        posts: {
            type: Array,
            required: true,
        }
    }

}
</script>

<style lang="scss" scoped>
h3{ 
    display: block;
    text-align: center;
    margin-top: 50px;
    margin-bottom: 50px;
}
</style>
