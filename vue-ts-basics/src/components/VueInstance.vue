<!--Create a Vue instance-->
var vm = new Vue({
  // options
})

<!--Data and Methods-->
// Our data object
var data = { a: 1 }

// The object is added to a Vue instance
var vm = new Vue({
  data: data
})

// Getting the property on the instance
// returns the one from the original data
vm.a == data.a // => true

// Setting the property on the instance
// also affects the original data
vm.a = 2
data.a // => 2

// ... and vice-versa
data.a = 3
vm.a // => 3

<!--set initial values to data that will use the properties later-->
data: {
  newTodoText: '',
  visitCount: 0,
  hideCompletedTodos: false,
  todos: [],
  error: null
}
<!--use of Object.freeze-->
var obj = {
  foo: 'bar'
}

Object.freeze(obj)

new Vue({
  el: '#app',
  data: obj
})

<div id="app">
  <p>{{ foo }}</p>
  <!-- this will no longer update `foo`! -->
  <button v-on:click="foo = 'baz'">Change it</button>
</div>
<!--$ being useful instance property that differentiate properties from user-defined properties-->
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})

vm.$data === data // => true
vm.$el === document.getElementById('example') // => true

// $watch is an instance method
vm.$watch('a', function (newValue, oldValue) {
  // This callback will be called when `vm.a` changes
})

<!--Instance Lifecycle Hooks: created, mounted, created, destroyed-->
<!--Each Vue instance goes through a series of initialization steps when it’s created - 
for example, it needs to set up data observation, compile the template, mount the instance to the DOM, 
and update the DOM when data changes. Along the way, it also runs functions called lifecycle hooks, 
giving users the opportunity to add their own code at specific stages.-->
new Vue({
  data: {
    a: 1
  },
  created: function () {
    // `this` points to the vm instance
    console.log('a is: ' + this.a)
  }
})
// => "a is: 1"
