<script setup>

</script>


<template>
    <nav class="navbar">
        <router-link :to="{name:'home'}">Projects </router-link>
        <router-link :to="{name:'AddProject'}">Add Project</router-link>
    </nav>
</template>



<style>
.navbar{
    text-align: center;
    margin: 40px auto;
}
.navbar a{
    display: inline-block;
    text-decoration: none;
    margin: 0 10px;
    color: #999;
    font-size: 18px;
}
a.router-link-active{
    border-bottom: 2px solid rgb(22, 222, 155);
    padding-bottom: 4px;
}
</style>