<template>
    <div class="guests" v-if="name">
        <p class="guests__name">Users:</p>
        <div class="guests__list" v-for="name in names">
            <p> {{ name.nick }} ;</p>
        </div>
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
            names: []
        }
    },
    methods: {
        publish: function() {
            this.$http.get('https://livechat-b3aa5.firebaseio.com/names.json').then(function(data){
                return data.json()
            }).then(function(data){
                var guestsArray = [];
                for (let key in data){
                    data[key].id = key;
                    guestsArray.push(data[key]);
                }
                this.names = guestsArray;
            });
        },
        check: function() {
            setInterval(this.publish, 500);
        }
    },
    created() {
        this.check();
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
