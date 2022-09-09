<template>
<div class="post-list">
    <div class="post-list_container" v-if="posts.length > 0">
        <h3>Последние записи:</h3>
        <post-item 
        :post="post"
        v-for="post in posts" :key="post.id"
        @delete="$emit('delete', post)"
         />
    
    </div>
    <h3 v-else>Тут пока нет записей</h3>
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

.post-list{
    min-height: fit-content;
}
</style>
