<!--Mapping an array to elements with v-for-->
<ul id="example-1">
  <li v-for="item in items" :key="item.message">
    {{ item.message }}
  </li>
</ul>

var example1 = new Vue({
  el: '#example-1',
  data: {
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})

<ul id="example-2">
  <li v-for="(item, index) in items">
    {{ parentMessage }} - {{ index }} - {{ item.message }}
  </li>
</ul>
var example2 = new Vue({
  el: '#example-2',
  data: {
    parentMessage: 'Parent',
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})

<div v-for="item of items"></div>

<!--v-for with an Object-->
<ul id="v-for-object" class="demo">
  <li v-for="value in object">
    {{ value }}
  </li>
</ul>

new Vue({
  el: '#v-for-object',
  data: {
    object: {
      title: 'How to do lists in Vue',
      author: 'Jane Doe',
      publishedAt: '2016-04-10'
    }
  }
})
//You can also provide a second argument for the property’s name (a.k.a. key):
<div v-for="(value, name) in object">
  {{ name }}: {{ value }}
</div>
//another for the index
<div v-for="(value, name, index) in object">
  {{ index }}. {{ name }}: {{ value }}
</div>
//To give Vue a hint so that it can track each node’s identity, and thus reuse and reorder existing elements, 
//you need to provide a unique key attribute for each item:
<div v-for="item in items" v-bind:key="item.id">  //Use string or numeric values for key
  <!-- content -->
</div>

<!--Array Change Detection-->
<ul id="example-1">
  <li v-for="item in items" :key="item.message">
    {{ item.message }}
  </li>
</ul>

var example1 = new Vue({
  el: '#example-1',
  data: {
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
<!--mutation methods: mutate the original array-->
push()
pop()
shift()
unshift()
splice()
sort()
reverse()
E.g. example1.items.push({message: 'Baz'})
<!--Replacing an Arrays: return a new array-->
filter()
concat()
slice()
E.g. example1.items = example1.items.filter(function (item) {
  return item.message.match(/Foo/)
})

<!--Displaying Filtered/Sorted Results-->
//create a computed property that returns the filtered or sorted array
<li v-for="n in evenNumbers">{{ n }}</li>

data: {
  numbers: [ 1, 2, 3, 4, 5 ]
},
computed: {
  evenNumbers: function () {
    return this.numbers.filter(function (number) {
      return number % 2 === 0
    })
  }
}
//use methods when computed properties are not feasible such as inside nested v-for loops
<ul v-for="set in sets">
  <li v-for="n in even(set)">{{ n }}</li>
</ul>

data: {
  sets: [[ 1, 2, 3, 4, 5 ], [6, 7, 8, 9, 10]]
},
methods: {
  even: function (numbers) {
    return numbers.filter(function (number) {
      return number % 2 === 0
    })
  }
}
//https://medium.com/swlh/filtering-sorting-and-searching-in-arrays-with-vue-js-f60951c040fc

<!--v-for with a Range-->
<div>
  <span v-for="n in 10">{{ n }} </span>
</div>
//result: 12345678910

<!--v-for on a <template>-->
// to render a block of multiple elements
<ul>
  <template v-for="item in items">
    <li>{{ item.msg }}</li>
    <li class="divider" role="presentation"></li>
  </template>
</ul>

<!--v-for with v-if-->
//v-for first, then v-if
<li v-for="todo in todos" v-if="!todo.isComplete">
  {{ todo }}
</li>
//But If instead, your intent is to conditionally skip execution of the loop, 
//you can place the v-if on a wrapper element (or <template>).
<ul v-if="todos.length">
  <li v-for="todo in todos">
    {{ todo }}
  </li>
</ul>
<p v-else>No todos left!</p>

<!--v-for with a Component-->
<my-component v-for="item in items" :key="item.id"></my-component>
//the code above doens't pass data to the component; use props
<my-component
  v-for="(item, index) in items"
  v-bind:item="item"
  v-bind:index="index"
  v-bind:key="item.id"
></my-component>
//to do list example
<div id="todo-list-example">
  <form v-on:submit.prevent="addNewTodo">
    <label for="new-todo">Add a todo</label>
    <input
      v-model="newTodoText"
      id="new-todo"
      placeholder="E.g. Feed the cat"
    >
    <button>Add</button>
  </form>
  <ul>
    <li
      is="todo-item"
      v-for="(todo, index) in todos"
      v-bind:key="todo.id"
      v-bind:title="todo.title"
      v-on:remove="todos.splice(index, 1)"
    ></li>
  </ul>
</div>

Vue.component('todo-item', {
  template: '\
    <li>\
      {{ title }}\
      <button v-on:click="$emit(\'remove\')">Remove</button>\
    </li>\
  ',
  props: ['title']
})

new Vue({
  el: '#todo-list-example',
  data: {
    newTodoText: '',
    todos: [
      {
        id: 1,
        title: 'Do the dishes',
      },
      {
        id: 2,
        title: 'Take out the trash',
      },
      {
        id: 3,
        title: 'Mow the lawn'
      }
    ],
    nextTodoId: 4
  },
  methods: {
    addNewTodo: function () {
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodoText
      })
      this.newTodoText = ''
    }
  }
})