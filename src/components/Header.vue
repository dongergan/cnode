<template>
    <div class="Header">
        <router-link :to="{
            name:'root'
        }">
            <img src="../assets/cnodejs_light.svg" alt="">
        </router-link>
        
        <ul>
            <li><a href="">首页</a></li>
            <li><a href="">新手入门</a></li>
            <li><a href="">API</a></li>
            <li><a href="">关于</a></li>
            <li><a href="">注册</a></li>
            <li><a href="">登陆</a></li>
        </ul>
    </div>
</template>


<script>
export default {
    name: "Header"
}
</script>
<style scoped>
.Header {
    background-color: #5a5555;
    height:50px;
}
a {
    text-decoration: none;
    color: #ccc;
    padding: 5px;
    margin:5px;
    text-shadow: none;
}
li {
    list-style:none;
    display:inline-block;
}
ul {
    float:right;
}
img {
    max-width: 120px;
    margin-left: 50px;
    margin-top: 10px;
}
</style>