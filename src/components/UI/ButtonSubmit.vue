<template>
    <div>
        <button type="submit" class="waves-effect waves-light light-blue darken-4 btn">Отправить</button> 
    </div>
</template>

<script>
    export default {
        name: "button-submit"
    }
</script>

<style lang="scss" scoped>
    .btn{
        align-self: flex-end;
        margin-top: 15px;
        background-color: #01579b; //#096683; // #0597c4;
        border-radius: 2px;
        border: none;
        font-weight: 500;
        color: #fff;
        cursor: pointer;
    }
   
</style>