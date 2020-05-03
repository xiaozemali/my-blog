<template>

 <nav>
    <ul>
        <li>
        <router-link to="/" exact>博客</router-link>
        <router-link to="/add" exact>写博客</router-link>
        </li>
    </ul>
 </nav>
</template>
<script>
export default {
    name:"blog-header"
}
</script>
<style scope>
nav{
    background: crimson;
    padding: 30px 20px;
    margin-bottom: 40px;
    max-width: 100%;
    margin: 0 auto;
}
ul{
    list-style: none;
    text-align: center;
    margin: 0;
}
li{
    display: inline-block;
    padding: 24px;
    margin: 0 10px;
}
a{
    text-decoration: none;
    color: #fff;
    padding: 12px;
    border-radius: 5px;
}
.router-link-active{
    background: rgba(255,255,255,0.8);
}
</style>