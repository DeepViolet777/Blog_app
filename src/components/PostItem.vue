<template>
<div>
    <div class="post">
        <div class="post-content">
            <h5 class="post-title">
                {{post.title}}
            </h5>
            <p class="post-body">
                {{post.body}}
            </p>
            <div class="img_wrapper" v-if="post.img">
                <img :src="post.img" class="post-img">
            </div>
        </div>
        <div class="post-btns">
            <button-delete @click="$emit('delete', post)" />
        </div>
    </div>
</div>
</template>

<script>
import ButtonDelete from "@/components/UI/ButtonDelete";

export default {
    components: {
        ButtonDelete
    },
    props: {
        post: {
            type: Object,
            requared: true,
        }
    }
}
</script>

<style lang="scss" scoped>
.post {
    text-align: left;
    display: block;
    padding: 15px;
    border: 2px solid #01579b; 
    border-radius: 5px;
    width: 600px;
    min-height: 150px;
    margin: 20px auto;
    background-color: #fff;
    display: flex;
    justify-content: space-between;

    &-body {
        margin-top: 15px;
    }

    h5 {
        display: block;
        width: 100%;
        height: auto;
    }

    &-img {
        max-width: 100%;
      }
    

    @media screen and (max-width: 1199px) {
        width: 600px;
        margin: 30px auto;
    }

    @media screen and (max-width: 767px) {
        width: 90%;
        margin: 30px auto;
    }
}
</style>
