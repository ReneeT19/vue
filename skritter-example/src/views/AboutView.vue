<template>
  <div class="about">
    <h1>This is an about page</h1>

    <div v-for="(user, i) in users" :key="i">
      {{ user.name }}
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

interface User {
  name: string;
}

@Component
export default class App extends Vue {
  users: User[] = [
    { name: 'Bob' },
    { name: 'Cheryl' }
  ]
}
</script>
