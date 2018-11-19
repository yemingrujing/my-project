<template>
  <div id="secondcomponent">
    <h1>I am another page</h1>
    <a>writen by {{author}}</a>
    <p>
      感谢
      <a href="https://github.com/showonne">showonne</a>
      大神的技术指导
    </p>
    <ul>
      <h1>{{title}}</h1>
      <li v-for="article in articles">
        <h2>{{article.title}}</h2>
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        author: "微信公众号 yemingrujing",
        articles: []
      }
    },
    mounted: function() {
      this.$http.jsonp('https://api.douban.com/v2/movie/top250?count=10', {}, {
        headers: {

        },
        emulateJSON: true
      }).then(function(response){
        // 这里是处理正确的回调
        this.title = response.data.title
        this.articles = response.data.subjects
        console.log(response.data.title)
        console.log(response.data.subjects)
        // this.articles = response.data["subjects"] 也可以
      }, function(response) {
        // 这里是处理错误的回调
        console.log(response)
      })
    }
  }
</script>
