<template>

<div id="single-blog">
<h1>{{blog.title}}</h1>
<article>{{blog.body}}</article>
</div>


</template>


<script>
export default {
    name:'single-blog',
    data(){
        return{
            id:this.$route.params.id,
            blog:{}
        }
        
    },
    mounted() {
        this.$http.get('https://jsonplaceholder.typicode.com/posts/'+this.id)
        .then(function(data){
            // console.log(data)
            this.blog=data.body;
        })
    },
}
</script>


<style scope>
#single-blog{
    max-width: 960px;
    border:1px black solid;
    padding: 30px;
    background: #eee;
    margin: 0 auto;
    border-radius: 14px;
    box-shadow: darkgray 5px 5px ;
}
</style>