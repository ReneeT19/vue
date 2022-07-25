<template>
    <div id="practice">
        <h1>
            {{ product }} are in stock.
        </h1>
        <ul>
          <li v-for="tab in tabs" :key="tab">
          {{ tab }}
          </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { Prop, Vue, Component } from 'vue-property-decorator'

// interface ProductList {
//     name: string
//     value: string
// }

@Component
export default class ThePractice extends Vue {
  @Prop({ default: 'Shoes' }) readonly product!: string;
  @Prop({ type: Array, required: true }) products!: string[];
  @Prop({ type: Array, default: () => { return ['default value'] } })
  tabs!: string[]

  // get formattedMessage (): string {
  //   return `<strong>${this.msg}</strong>`
  // }

  // Fetch API
  // created () {
  //   fetch('url')
  //   .then(response => response.json())
  //   .then(json => {
  //     this.products = json.products
  //   })
  // }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
