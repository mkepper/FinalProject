<template>
    <div class = "header">
        <h1>{{theTitle}}</h1>
    </div>
</template>

<script>
export default {
    name: "Header",
    props: ['theTitle']
}
</script>

<style scoped>
.header{
    color: black;
    background-color: gray;
    width: 50%;
    margin: auto;
    padding: 10px;
}
</style>