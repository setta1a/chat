<template>
    <div class="container">
        <slot></slot>
    </div>
</template>

<style>
    .container {
        width: 764px;
        margin: auto;
        box-shadow: 0 0 15px 0 #5f5f5f73;
    }
</style>

<script>
    export default{
        name: "ContainerVue"
    }
</script>