<template>
    <div class="posts">
  <div v-for="post in posts">
      <p>{{ post.content }}</p>
  </div>
    </div>
</template>

<script>
export default {
  
  data () {
    return {
        posts: []
    }
  },
  methods: {

  },
  created() {
        this.$http.get('https://livechat-b3aa5.firebaseio.com/posts.json').then(function(data){
            return data.json()
        }).then(function(data){
            var postsArray = [];
            for (let key in data){
                data[key].id = key;
                postsArray.push(data[key]);
            }
            this.posts = postsArray;
            console.log(this.posts);
        });
  }
}
</script>

<style lang="scss">
    .posts {
        width: 70vw;
        height: 50vh;
        border: 1px solid black;
    }
</style>
