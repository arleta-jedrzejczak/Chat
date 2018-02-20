<template>
  <div>
    <label>Your message: <textarea v-model="message.content"></textarea></label>
    <p>Preview: {{ message.content }}</p>
    <button v-on:click.prevent="post">Send</button>
  </div>
</template>

<script>
export default {
  
  data () {
    return {
        message: {
        content: ''
        }
    }
  },
  methods: {
        post: function(){
            this.$http.post('https://livechat-b3aa5.firebaseio.com/posts.json', this.message).then(function(data){
                console.log(data);
                this.message.content = '';
            });
        }
  }
}
</script>

<style lang="scss">

</style>
