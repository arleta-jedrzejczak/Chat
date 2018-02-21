<template>
  <div class="writer" v-show="name">
    <label class="writer__message">Your message: <textarea class="writer__field" v-model="message.content"></textarea></label>
    <button class="writer__button" v-on:click.prevent="post">Send</button>
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
            },
            event: {}
        }
    },
    methods: {
        post: function(){
            this.message.author = this.name;
            this.$http.post('https://livechat-b3aa5.firebaseio.com/posts.json', this.message).then(function(data){
                this.message.content = '';
            });
        }
    }
}
</script>

<style lang="scss">

</style>
