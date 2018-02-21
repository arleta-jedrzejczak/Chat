<template>
  <div class="container">
    <div class="login" v-if="!name">
      <label class="login__name">Name: <input class="login__input" v-model="guest" id="username" type="text" placeholder="Your name"></label>
      <button class="login__submit" v-on:click.prevent="save">Let's chat</button>
    </div>
    <app-screen v-bind:name="name"></app-screen>
    <app-writer v-bind:name="name"></app-writer>
    <app-guests v-bind:name="name"></app-guests>
  </div>
</template>

<script>

import screen from './components/screen.vue'
import writer from './components/writer.vue'
import guests from './components/guests.vue'

export default {
  
  components: {
    'app-screen': screen,
    'app-writer': writer,
    'app-guests': guests
  },
  data () {
    return {
      guest: '',
      name: '',
      visitor: {
        nick: ''
      }

    }
  },
  methods: {
    save: function() {
        if(this.guest != '') {
        this.name = this.guest;
        this.visitor.nick = this.guest;
          this.$http.post('https://livechat-b3aa5.firebaseio.com/names.json', this.visitor).then(function(data){
        });
      }
      else {
        alert('Please, fill in your name');
      }
    }
  }
}
</script>

<style lang="scss">


</style>
