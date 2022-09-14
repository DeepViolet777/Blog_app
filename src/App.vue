<template>
<div class="app light-blue lighten-5">
    <post-form @create="createPost" />
    <post-list :posts="posts" @delete="deletePost" />
</div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import axios from 'axios/dist/axios.min';

export default {
    components: {
        PostForm,
        PostList
    },

    data() {
        return {
            posts: [],

        }
    },
    methods: {
        createPost(post) {
            this.posts.unshift(post);
        },
        deletePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id);
        },
        async getPosts() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
                this.posts = response.data;
                console.log(response)
            } catch (error) {
                console.log(error)
            }
        }      
    },
    mounted() {
            this.getPosts();
        }
}
</script>

<style lang="scss">
@import "materialize-css/dist/css/materialize.min.css";

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    width: 100%;
    height: 100%;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}

.app {
    padding: 3%;
    width: 100%;
    min-height: 100vh;

}
</style>
