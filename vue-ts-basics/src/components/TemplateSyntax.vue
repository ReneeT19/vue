<!--Interpolations-->
<span>Message: {{ msg }}</span>

<span v-once>This will never change: {{ msg }}</span> //v-once directive do not update on data 🉐 

<p>Using mustaches: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p> //use v-html to render real html (words in red)

//Attributes
<div v-bind:id="dynamicId"></div>
<button v-bind:disabled="isButtonDisabled">Button</button>

//JS expressions
{{ number + 1 }}
{{ ok ? 'YES' : 'NO' }}
{{ message.split('').reverse().join('') }}
<div v-bind:id="'list-' + id"></div>

<!--Directives-->
<p v-if="seen">Now you see me</p>
//take argument (href, event name to listen to)
<a v-bind:href="url"> ... </a>
<a v-on:click="doSomething"> ... </a>
//dynamic arguments
<a v-bind:[attributeName]="url"> ... </a>
<a v-on:[eventName]="doSomething"> ... </a>
<!-- This will trigger a compiler warning. -->
<a v-bind:['foo' + bar]="value"> ... </a>
//modifiers: the .prevent modifier tells the v-on directive to call event.preventDefault() on the triggered event
<form v-on:submit.prevent="onSubmit"> ... </form>
<!--v-bind shorthand-->
<!-- full syntax -->
<a v-bind:href="url"> ... </a>

<!-- shorthand -->
<a :href="url"> ... </a>

<!-- shorthand with dynamic argument (2.6.0+) -->
<a :[key]="url"> ... </a>
<!--v-on shorthand-->
<!-- full syntax -->
<a v-on:click="doSomething"> ... </a>

<!-- shorthand -->
<a @click="doSomething"> ... </a>

<!-- shorthand with dynamic argument (2.6.0+) -->
<a @[event]="doSomething"> ... </a>
