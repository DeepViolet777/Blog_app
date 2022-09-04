<template>
<div>
    <div class="post" v-for="post in posts" :key="post.id">
        <h4 class="post-title">
            {{post.title}}
        </h4>
        <p class="post-body">
            {{post.body}}
        </p>
    </div>
</div>
</template>

<script>
export default {
    props: {
        posts: {
            type: Array,
            required: true,
        }
    }
}
</script>

<style lang="scss" scoped>
.post {
    text-align: left;
    display: block;
    padding: 15px;
    border: 2px solid #01579b;//#096683; 
    border-radius: 5px;
    width: 30%;
    height: 10%;
    margin: 20px auto;

    &-body {
        margin-top: 15px;
    }

}
</style>
