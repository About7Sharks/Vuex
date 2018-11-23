<template>
  <div class="stats">
    <h1>Statistics</h1>
    <p>There are currently {{ countLinks}} links</p>
    <button v-on:click="removeAllLinks">Remove All Items</button>
    <p v-if="countLinks <= 0">{{msg}}</p>
  </div>
</template>

<script>
import {mapGetters, mapMutations, mapActions} from 'vuex'
export default {
  name: 'stats',
  data(){
    return{
      msg:''
    }
  },
  computed: {
    ...mapGetters([
      'countLinks'
      ]),
    //other stuff
  },
  methods:{
    ...mapMutations(['REMOVE_ALL']),
    ...mapActions(['removeLinks']),
    removeAllLinks(){
      this.removeLinks().then(()=>{
        this.msg= 'Everything has been removed'
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
button{
  padding: 10px;
  margin-top: 30px;
  background: none;
  border: 1px solid lightgray;
  outline: 0;
  cursor: pointer;
}
</style>
