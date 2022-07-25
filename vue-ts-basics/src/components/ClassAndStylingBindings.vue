<!--Binding HTML Classes-->
<!--Object Syntax-->
<div v-bind:class="{ active: isActive }"></div>
//v-bind directive co-exists with the plain class attribute
<div
  class="static"
  v-bind:class="{ active: isActive, 'text-danger': hasError }"
></div>
data: {
  isActive: true,
  hasError: false
}
//it will render
<div class="static active"></div>
//alternatively, the bound object is not inline
<div v-bind:class="classObject"></div>
data: {
  classObject: {
    active: true,
    'text-danger': false
  }
}
//bind to a computed property
<div v-bind:class="classObject"></div>
data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}

<!--Array Syntax-->
<!--We can pass an array to v-bind:class to apply a list of classes:-->
<div v-bind:class="[activeClass, errorClass]"></div>
data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
//it will render
<div class="active text-danger"></div>
//condition - toggle
<div v-bind:class="[isActive ? activeClass : '', errorClass]"></div> 
//verbose, you can use the object syntax inside array syntax
<div v-bind:class="[{ active: isActive }, errorClass]"></div>

<!--With Components-->
<!--When you use the class attribute on a custom component, those classes will be added to the component’s root element. 
Existing classes on this element will not be overwritten.-->
Vue.component('my-component', {
  template: '<p class="foo bar">Hi</p>'
})
<my-component class="baz boo"></my-component>
//it will render 
<p class="foo bar baz boo">Hi</p>
<my-component v-bind:class="{ active: isActive }"></my-component>
//it will render
<p class="foo bar active">Hi</p>

<!--Binding Inline Styles-->
<!--Object Syntax: often used with ocmputed properties-->
<div v-bind:style="styleObject"></div>
data: {
  styleObject: {
    color: 'red',
    fontSize: '13px'
  }
}

<!--Array Syntax-->
<div v-bind:style="[baseStyles, overridingStyles]"></div>
//give an array of multiple (prefixed) values to a style property
<div v-bind:style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>



