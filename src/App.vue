<template>
  <div>
    <div>
      <label>Name: <input v-model="name" id="username" type="text" placeholder="Your name"></label>
    </div>
    <app-screen></app-screen>
    <app-writer v-bind:name="name"></app-writer>
  </div>
</template>

<script>

import screen from './components/screen.vue'
import writer from './components/writer.vue'

export default {
  
  components: {
    'app-screen': screen,
    'app-writer': writer
  },
  data () {
    return {
      name: ''

    }
  }
}
</script>

<style lang="scss">

</style>
