<template>
<div>
    <div class="post">
        <div class="post-content">
            <h4 class="post-title">
                {{post.title}}
            </h4>
            <p class="post-body">
                {{post.body}}
            </p>
        </div>
        <div class="post-btns">
            <button-delete @click="$emit('delete', post)"/>
        </div>
    </div>
</div>
</template>

<script>
import  ButtonDelete from "@/components/UI/ButtonDelete";

export default {
    components: {ButtonDelete},
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
    border: 2px solid #01579b; //#096683; 
    border-radius: 5px;
    width: 30%;
   // height: 10%;
    margin: 20px auto;
    background-color: #fff;
    display: flex;
    align-items: center;
    justify-content: space-between;

    &-body {
        margin-top: 15px;
    }

    @media screen and (max-width: 575px) {
        width: 90%;
       // height: 10%;
    }
}
</style>
