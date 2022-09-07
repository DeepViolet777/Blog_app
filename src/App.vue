<template>
<div class="app light-blue lighten-5">
    <post-form @create="createPost" />
    <post-list :posts="posts" />

</div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

export default {
    components: {
        PostForm,
        PostList
    },

    data() {
        return {
            posts: [{
                    id: 1,
                    title: "Заголовок 1",
                    body: "Текст 1"
                },
                {
                    id: 2,
                    title: "Заголовок 2",
                    body: "Текст 2"
                },
                {
                    id: 3,
                    title: "Заголовок 3",
                    body: "Текст 3"
                },
                {
                    id: 4,
                    title: "Заголовок 4",
                    body: "Текст 4"
                },
            ],

        }
    },
    methods: {
        createPost(post) {
            this.posts.unshift(post);
        }
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

}
</style>
