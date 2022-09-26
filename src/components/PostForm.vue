<template>
<div class="form-container">
    <form class="form" @submit.prevent>
        <h4>Создать пост</h4>
        <input type="text" class="input input-text validate" required placeholder="Заголовок" v-model="post.title" @blur="v$.post.title.$touch" />
        <!-- :class="{invalid:($v.post.title.$dirty && !$v.post.title.required)}"/> -->
        <!-- @blur="v$.post.title.$touch" -->
        <span v-if="v$.post.title.$error" style="color:red">Введите текст</span>
        <!-- <span class="helper-text" data-error="Введите текст"></span> -->
        <input type="text" class="input input-text materialize-textarea validate" required placeholder="Текст поста" v-model="post.body" @blur="v$.post.body.$touch" />
        <span v-if="v$.post.body.$error" style="color:red">Введите текст</span>
        <!-- <span class="helper-text" data-error="Введите текст"></span> -->
        <!-- <textarea class="input input-textarea validate" placeholder="Текст поста" v-model="post.body" required /> -->
        <!-- <input type="file" name="" id="" @change="checkFile($event)" > -->
       
        <img-loader/>
        <button type="submit" class="waves-effect waves-light light-blue darken-4 btn" :disabled="v$.$invalid" @click="createPost">Отправить</button>
    </form>
</div>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import {required} from '@vuelidate/validators'
import ImgLoader from '@/components/UI/ImgLoader.vue'

export default {
  components: { ImgLoader },
    setup() {
        return {
            v$: useVuelidate()
        }
    },
    data() {
        return {
            post: {
                title: "",
                body: "",
               
            }

        }
    },

    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit('create', this.post);
            this.post = {
                title: "",
                body: "",
                
            }
            this.v$.$reset();
            // this.$forceUpdate(); 
            const inputs = document.querySelectorAll(".input-text");
            inputs.forEach(input => {
                input.classList.remove('valid');
            });

        },
       

    },
    validations: {
        post: {
            title: {
                required
            },
            body: {
                required
            },
        }
    },
}
</script>

<style lang="scss" scoped>
.form {
    width: 600px;
    display: flex;
    flex-direction: column;
    padding: 10px 15px;
    margin: 20px auto;
    border: 2px solid #01579b; //#096683;
    border-radius: 5px;
    background-color: #fff;

    @media screen and (max-width: 1199px) {
        width: 600px;
        margin: 0 auto;
    }

    @media screen and (max-width: 767px) {
        width: 90%;
        margin: 0 auto;
    }
}

.input {
    width: 100%;
    border: 2px solid #0277bd; //#01579b;//#096683;
    border-radius: 5px;
    padding: 10px 15px;
    margin-top: 15px;

    &-textarea {
        height: 120px;
    }
}



</style>
