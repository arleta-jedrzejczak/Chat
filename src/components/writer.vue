<template>
  <div v-if="name">
    <label>Your message: <textarea v-model="message.content"></textarea></label>
    <p>{{ name }} is writing: {{ message.content }}</p>
    <button v-on:click.prevent="post">Send</button>
  </div>
</template>

<script>
export default {
    props: {
        name: {
            type: String
        }
    },
  data () {
    return {
        message: {
        content: '',
        author: ''
        }
    }
  },
  methods: {
        post: function(){
            this.message.author = this.name;
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
