<template>
<div id="show-blogs">
<h1>博客总览</h1>
<input type="text" placeholder="搜索" v-model="search">
<div v-for="(blog,index) in filteredBlogs"  :key="index" class="single-blog" >
<router-link :to="'/blog/'+blog.id">
<h2 v-rainbow>{{blog.title | to-uppercase}}</h2>
</router-link>
<article>
{{blog.body | snippet}}
</article>
</div>
</div>
</template>
<script>
export default {
    name:'show-blogs',
    data() {
        return {
            blogs:[],
            search:''
        }
    },
    created(){
        this.$http.get('https://jsonplaceholder.typicode.com/posts')
        .then(function(data){
            // console.log(data);
            this.blogs=data.body.slice(0,10);
            // console.log(this.blogs);
        })
    },
    computed:{
        filteredBlogs:function(){
            return this.blogs.filter((blog)=>{
                return blog.title.match(this.search);
            })
        }
    }
}
</script>
<style>
#show-blogs{
    max-width: 800px;
    margin: 0 auto;
    background: #6677ee;
    padding: 20px;
}
.single-blog{
    margin: 20px auto;
    padding:20px ;
    box-sizing: border-box;
    background: #eee;
}
input[type="text"]{
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
}
</style>