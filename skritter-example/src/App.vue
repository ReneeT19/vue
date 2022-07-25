<template>
  <div id="app">
      <PracticeVueComponent product = "Socks" tabs = "A B C"/>
      <HelloWorldComponent />
    <!-- <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      <button class="alert-button" @click="showAlert('hello world')">show alert</button>
    </nav>
    <router-view/> -->
  </div>

</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import PracticeVueComponent from '@/components/ThePractice.vue'
import HelloWorldComponent from '@/components/HelloWorld.vue'

// Example of not using the vue-property-decorator library
// export default {
//   name: 'App',
//   components: {
//     PracticeVueComponent,
//     HelloWorldComponent
//   }
// }

// Example of using the vue-property-decorator library
// Register components here and use it in template
@Component({
  components: { PracticeVueComponent, HelloWorldComponent }
})
export default class App extends Vue {
  // showAlert (value: string) {
  //   alert(value)
  // }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
  text-align: center;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.alert-button {
  display: block;
  margin: 30px auto 0 auto;
  text-transform: uppercase;
}
</style>
