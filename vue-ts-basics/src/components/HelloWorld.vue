<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ firstName }}</h1>
    <h1>{{ lastName }}</h1>
    <h1>{{ fullName }}</h1>
    <h5>{{ counter }}</h5>
    <button @click="incrementCounter()">Click me</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
//variables
  firstName = "Renee"
  lastName = "Thomsen"
  counter = 0;
  zip: string|undefined; //use Typescript here to restrict variable type

//lifecycle hooks
  mounted() {
    console.log('mounted')
  }

//computed properties (getters) with Typescript type "string"
  get fullName(): string{
    return this.firstName + " " + this.lastName;
  }
//methods
  incrementCounter() {
    this.zip = "10086";
    this.counter++;
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
</style>
