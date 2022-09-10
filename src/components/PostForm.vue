<template>
<div class="form-container">
    <form class="form" @submit.prevent>
        <h4>Создать пост</h4>
        <input type="text" class="input validate" placeholder="Заголовок" v-model="post.title" required />
        <!-- <span class="helper-text" data-error="Введите текст"></span> -->
        <input type="text" class="input input-textarea validate" placeholder="Текст поста" v-model="post.body" required />
        <!-- <span class="helper-text" data-error="Введите текст"></span> -->
        <!-- <textarea class="input input-textarea validate" placeholder="Текст поста" v-model="post.body" required /> -->
        <!-- <input type="file" name="" id="" @change="checkFile($event)" > -->
        <div class="file-field input-field">
            <div class="btn btn-file">
                <i class="material-icons">attach_file</i>
                <span>Загрузить фото</span>
                <input type="file">
            </div>
            <div class="file-path-wrapper">
                <input class="file-path validate" type="text">
            </div>
        </div>
        <button type="submit" class="waves-effect waves-light light-blue darken-4 btn" @click="createPost">Отправить</button>
    </form>
</div>
</template>

<script>
import useVuelidate from '@vuelidate/core'
import {required} from '@vuelidate/validators';
export default {
    //   mixins: [validationMixin],
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
        }

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
    }
}
</script>

<style lang="scss" scoped>
.form {
    width: 40%;
    display: flex;
    flex-direction: column;
    padding: 10px 15px;
    margin: 20px auto;
    border: 2px solid #01579b; //#096683;
    border-radius: 5px;
    background-color: #fff;

    @media screen and (max-width: 1199px) {
        width: 65%;
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

.btn {
    //width: 100px;
    // padding: 10px 15px;
    align-self: flex-end;
    margin-top: 15px;
    background-color: #01579b; //#096683; // #0597c4;
    //  border: 2px solid #096683;
    border-radius: 2px;
    border: none;
    font-weight: 500;
    color: #fff;
    cursor: pointer;
    //transition: .2s;

    //   &:hover {
    //      background-color: #0277bd;//#0b799b;
    //    }

    //   &:active {
    //       background-color: #039be5;//#0e96c0;
    //    }

    &-file {
        display: flex;
        justify-content: space-between;
        font-size: 11px;
        line-height: 12px;
        font-weight: 600;
        vertical-align: middle;
        padding-left: 5px;
        padding-right: 10px;

        i {
            margin-right: 4px;
        }

    }
}

.file-field span {

    // font-size: 12px;

    //height: 2rem;

}

.file-field input[type=file] {
    //   font-size: 12px;
    font-weight: 500;
    height: 2rem;
}
</style>
