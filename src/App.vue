<template>
<div class="app light-blue lighten-5">
    <post-form @create="createPost" />
    <post-list :posts="posts" @delete="deletePost" />
    <v-pagination v-model="page" :pages="10" :range-size="1" active-color="#DCEDFF" @update:modelValue="updateHandler" />
</div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import axios from 'axios/dist/axios.min';

export default {
    components: {
        PostForm,
        PostList,

    },

    data() {
        return {
            posts: [],
            page: 10
        }
    },
    methods: {
        createPost(post) {
            this.posts.unshift(post);
            this.setLocalPosts();
        },
        deletePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id);
            this.setLocalPosts();
        },
        async getPosts() {
            try {
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
                this.posts = response.data;
            } catch (error) {
                console.log(error)
            }
            
            this.setLocalPosts();
        },

        setLocalPosts() {
            localStorage.setItem('posts', JSON.stringify(this.posts));
        },

        getLocalPosts(){
            this.posts = JSON.parse(localStorage.getItem('posts'));
        }

    },

    mounted() {
        if (localStorage.getItem('posts')!= undefined){
            this.getLocalPosts();
             } else{
                this.getPosts();  
             }
            
    },
    // watch: {
    //     posts(newPost) {
    //         localStorage.posts = newPost;
    //     }
    // }
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

.btn {
    align-self: flex-end;
    margin-top: 15px;
    background-color: #01579b; //#096683; // #0597c4;
    //  border: 2px solid #096683;
    border-radius: 2px;
    border: none;
    font-weight: 500;
    color: #fff;
    cursor: pointer;

}
</style>
