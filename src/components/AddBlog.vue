<template>
  <div id="add-blog">
    <h2>添加博客</h2>
    <form v-show="!submmited">
      <label>博客标题</label>
      <input type="text" v-model="blog.title" required />
      <p>
        <label>博客内容</label>
        <textarea v-model="blog.content"></textarea>
      </p>

      <div id="checkboxes">
        <label>Vue.js</label>
        <input type="checkbox" value="Vue.js" v-model="blog.categories" />
        <label>Node.js</label>
        <input type="checkbox" value="Node.js" v-model="blog.categories" />
        <label>React.js</label>
        <input type="checkbox" value="React.js" v-model="blog.categories" />
        <label>Angular.js</label>
        <input type="checkbox" value="Angular.js" v-model="blog.categories" />
      </div>
      <label>博客作者:</label>
      <select v-model="blog.author">
        <option v-for="(author,index) in authors" :key="index">{{author}}</option>
      </select>
      <button @click.prevent="post">添加</button>
    </form>
    
    <div v-if="submmited">
    <h3>你的博客添加成功</h3>
    </div>

    <hr />
    <div id="preview">
      <h3>博客总览</h3>
      <p>博客标题:{{blog.title}}</p>
      <p>博客内容：</p>
      <p>{{blog.content}}</p>
      <p>博客分类</p>
      <ul>
        <li v-for="(category,index) in blog.categories" :key="index">{{category}}</li>
      </ul>
      <p>作者：{{blog.author}}</p>
    </div>
  </div>
</template>
<script>
export default {
  name: "add-blog",
  data() {
    return {
      blog: {
        title: "",
        content: "",
        categories: [],
        author: "",
        submmited:false
      },
      authors: ["jiaze", "ccc", "huanghuijin"]
    };
  },
  methods: {
    post: function() {
      this.$http
        .post("https://jsonplaceholder.typicode.com/posts", {
          title: this.blog.title,
          body: this.blog.content,
          userId: 1
        })
        .then(function(data) {
          this.submmited=true;
        });
    }
  }
};
</script>
<style  scoped>
#add-blog *{
  box-sizing: border-box;
  list-style:none ;
}
#add-blog{
  margin: 20px auto;
  max-width: 600px;
  padding: 20px;
}
label{
  display: block;
  margin: 20px 0 10px;
}
input[type="text"],textarea,select{
  display: block;
  width: 100%;
  padding: 8px;
}
textarea{
  height: 200px;
}
#checkboxes label{
  display: inline-block;
  margin-top: 0;
}
#checkboxes input{
  display: inline-block;
  margin-right:10px;
}
button{
  display: block;
  margin: 20px 0;
  background: crimson;
  color: #ffffff;
  padding: 14px;
  border-radius: 4px;
  font-size: 18px;
  border: 0px;
  cursor: pointer;
}
#preview{
  padding: 10px 20px;
  border: 1px dotted #cccccc;
  margin: 30px 0;
}
h3{
  margin-top: 10px;
}
</style> 