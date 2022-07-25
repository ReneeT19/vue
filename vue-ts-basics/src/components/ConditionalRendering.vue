<!--v-if-->
<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>
//toggle more than one element: use template
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
//v-else block
<div v-if="Math.random() > 0.5">
  Now you see me
</div>
<div v-else>
  Now you don't
</div>
//v-else-if
<div v-if="type === 'A'">
  A
</div>
<div v-else-if="type === 'B'">
  B
</div>
<div v-else-if="type === 'C'">
  C
</div>
<div v-else>
  Not A/B/C
</div>
//control reusable elements with key
<template v-if="loginType === 'username'">
  <label>Username</label>
  <input placeholder="Enter your username" key="username-input">
</template>
<template v-else>
  <label>Email</label>
  <input placeholder="Enter your email address" key="email-input">
</template>

<!--v-show-->
<h1 v-show="ok">Hello!</h1>
<!--an element with v-show will always be rendered and remain in the DOM; 
v-show only toggles the display CSS property of the element.
v-show doesn’t support the <template> element, nor does it work with v-else-->
//use v-show if you need to toggle something very often, and prefer v-if if the condition is unlikely to change at runtime
