<template>
  <div class="app">
    <!-- demo code -->
    <!-- <p>{{ name }} - {{ age }}</p>
    <button @click="changeName('Zelda')">change name</button>
    <button @click="changeAge(30)">change age</button> -->

    <!-- <p> {{ jobs[0].location }} </p> -->
    <JobList :jobs="jobs"/>

  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue';
import Job from '@/types/Job'
import JobList from './components/JobList.vue'

//Options API

// export default defineComponent({
//   name: 'App',
//   components: {},
//   data() { //TS knows data object is a string without specifying it
//     return {
//       name: 'Link',
//       age: 25 as number | string //age could be either a number or string - type casting/assertion within data object
//     }
//   },
//   methods: {//specify the type of name to be string
//     changeName(name: string) {
//       this.name = name; //this.name refers to the property name Link; name refers to the argument in this method
//       return name 
//     },
//     changeAge(age: string | number) { //you can also do age: string or age: number
//       this.age = age;
//       return age;
//     }
//   }
// });


//Composition API
export default defineComponent({
  name: 'App',
  components: {JobList},
  setup() {
    // //using reactive
    // const state = reactive({
    //   name: 'Link',
    //   age: 25 as string | number
    // })
    // //change the property but can't change type
    // state.name = 'Zelda'
    // state.age = 18

    // return { ...toRefs(state)}

    // // using refs: recommended
    // const name = ref('Link')
    // const age = ref<number | string>(21) //using generic type
    // // age.value = '37' would work
    // return { name, age }

    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1'},
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
    ])
    //pass jobs as props to print on the browser

    return { jobs }
  },
  // methods: {//specify the type of name to be string
  //   changeName(name: string) {
  //     this.name = name; //this.name refers to the property name Link; name refers to the argument in this method
  //     return name 
  //   },
  //   changeAge(age: string | number) { //you can also do age: string or age: number
  //     this.age = age;
  //     return age;
  //   }
  // }
});
</script>



<style>

</style>
