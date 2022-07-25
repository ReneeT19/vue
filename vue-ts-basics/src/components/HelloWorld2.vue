<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ test }}</h1>

    <button @click="incrementCounter()">Click me</button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'HelloWorld',
  props: {
      msg: String,
  },
  data(){
      return {
          test: "Hello From TS" as String
      }
  },
  methods: {
      pressMe(): String {
          return this.test + "string";
      }
  }
});
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
</style>
