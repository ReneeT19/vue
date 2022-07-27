<!--Base Example-->
// Define a new component called button-counter
Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
})

<div id="components-demo">
  <button-counter></button-counter>
</div>

new Vue({ el: '#components-demo' })

<!--Since components are reusable Vue instances, 
they accept the same options as new Vue, such as data, computed, watch, methods, and lifecycle hooks. -->
<!-- you can reuse components and each time a new instance is created, therefore the data must be a function instead of an object -->
<div id="components-demo">
  <button-counter></button-counter>
  <button-counter></button-counter>
  <button-counter></button-counter>
</div>


<!--Organizing Components-->
<!-- global registration: can be used in the template of any root vue instance (new Vue) -->
Vue.component('my-component-name', {
  // ... options ...
})


<!-- Passing Data to Child Components with Props -->
<!-- Props are custom attributes you can register on a component. 
When a value is passed to a prop attribute, it becomes a property on that component instance. -->
Vue.component('blog-post', {
  props: ['title'],
  template: '<h3>{{ title }}</h3>'
})

<blog-post title="My journey with Vue"></blog-post>
<blog-post title="Blogging with Vue"></blog-post>
<blog-post title="Why Vue is so fun"></blog-post>
<!-- typical app will have an array of posts in data -->
new Vue({
  el: '#blog-post-demo',
  data: {
    posts: [
      { id: 1, title: 'My journey with Vue' },
      { id: 2, title: 'Blogging with Vue' },
      { id: 3, title: 'Why Vue is so fun' }
    ]
  }
})
<!-- use v-bind to dynamically pass props; useful when fetching posts from API -->
<blog-post
  v-for="post in posts"
  v-bind:key="post.id"
  v-bind:title="post.title"  
></blog-post>


<!-- A Single Root Element -->
<!-- <div class="blog-post">
  <h3>{{ title }}</h3>
  <div v-html="content"></div>
</div> -->

<!-- a single post prop instead of listing all properties -->
<blog-post
  v-for="post in posts"
  v-bind:key="post.id"
  v-bind:post="post"
></blog-post>
Vue.component('blog-post', {
  props: ['post'],
  template: `
    <div class="blog-post">
      <h3>{{ post.title }}</h3>
      <div v-html="post.content"></div>
    <!-- </div> -->
  `
})


<!--Listening to Child Components Events-->
<!-- parent -->
new Vue({
  el: '#blog-posts-events-demo',
  data: {
    posts: [/* ... */],
    postFontSize: 1
  }
})

<div id="blog-posts-events-demo">
  <div :style="{ fontSize: postFontSize + 'em' }">
    <blog-post
      v-for="post in posts"
      v-bind:key="post.id"
      v-bind:post="post",
      v-on:enlarge-text="postFontSize += 0.1"
    ></blog-post>
  </div>
</div>

<!-- child -->
<button v-on:click="$emit('enlarge-text')">
  Enlarge text
</button>

<!-- Content Distribution with Slots -->
<!--pass content to a component-->
<alert-box>
  Something bad happened.
</alert-box>

Vue.component('alert-box', {
  template: `
    <div class="demo-alert-box">
      <strong>Error!</strong>
      <slot></slot>
    </div>
  `
})

<!-- Dynamic Components -->
<!-- Component changes when currentTabComponent changes -->
<component v-bind:is="currentTabComponent"></component>
