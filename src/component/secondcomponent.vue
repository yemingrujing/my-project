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
      <h1>{{jsonData.title}}</h1>
      <li v-for="(item, index) in articles">
        <h2>
          {{index + 1}} - <a :href="item.alt" target="_blank">{{item.title}}</a>
          <img  v-bind:src="getImages(item.casts[0].avatars.large)"/>
        </h2>
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        author: "微信公众号 yemingrujing",
        jsonData: [],
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
        this.jsonData = response.data
        this.articles = response.data.subjects
        console.log(response.data.subjects)
        // this.articles = response.data["subjects"] 也可以
      }, function(response) {
        // 这里是处理错误的回调
        console.log(response)
      })
    },methods: {
      getImages(_url) {
        if( _url !== undefined ){
          let _u = _url.substring( 7 );
          return 'https://images.weserv.nl/?url=' + _u;
        }
      }
    }
  }
</script>

<style media="screen">
  li {
    display:inline
  }
</style>
