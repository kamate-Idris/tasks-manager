<template>
    <button @click="onClick()" :style="{background : color}" class="btn">{{ text }}</button>
</template>

<script>
export default {
    name : "Button",
    props : {
        text : {
            type : String,
        },
        color : {
            type : String,
            default : 'black'
        }
        
    },
    methods : {
        onClick() {
            this.$emit('btn-click')
        }
    }
}
</script>

<style>
.btn {
    padding: 10px 20px;
    color: white;
    border-radius: 5px;
    font-size: 18px;
    cursor: pointer;
    border: none;

}
</style>