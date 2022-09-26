<template>
<div>
    <div class="imagePreviewWrapper" :style="{ 'background-image': `url(${previewImage})` }" @click="selectImage">
    </div>

    <div class="file-field input-field">
        <div class="btn btn-file">
            <i class="material-icons">attach_file</i>
            <span>Загрузить фото</span>
            <input type="file" ref="fileInput" @input="pickFile" />
        </div>
        <div class="file-path-wrapper">
            <input class="file-path validate" type="text">
        </div>
    </div>
</div>
</template>

  
<script>
export default {
    name: "img-loader",
    data() {
        return {
            previewImage: null
        };
    },
    methods: {
        selectImage() {
            this.$refs.fileInput.click()
        },
        pickFile() {
            let input = this.$refs.fileInput
            let file = input.files
            if (file && file[0]) {
                let reader = new FileReader
                reader.onload = e => {
                    this.previewImage = e.target.result
                }
                reader.readAsDataURL(file[0])
                this.$emit('input', file[0])
            }
        }
    }
}
</script>

  
<style lang="scss" scoped>
.imagePreviewWrapper {
    min-width: 250px;
    min-height: 250px;
    display: block;
    cursor: pointer;
    margin: 15px auto 30px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center center;
}

.btn {

    &-file {
        display: flex;
        justify-content: space-between;
        font-size: 11px;
        line-height: 3rem;
        font-weight: 600;
        vertical-align: middle;
        padding-left: 5px;
        padding-right: 10px;

        i {
            margin-right: 4px;
        }

    }

    .file-field .btn {
        height: 3rem;
    }
}
</style>
