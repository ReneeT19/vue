<!--Basic Usage: v-model-->
<!--text and textarea elements use value property and input event;
checkboxes and radiobuttons use checked property and change event;
select fields use value as a prop and change as an event.-->

<!--Text-->
<input v-model="message" placeholder="edit me">
<p>Message is: {{ message }}</p>

<span>Multiline message is:</span>
<p style="white-space: pre-line;">{{ message }}</p>
<br>
<textarea v-model="message" placeholder="add multiple lines"></textarea>

<!--Checkbox-->
<input type="checkbox" id="checkbox" v-model="checked">
<label for="checkbox">{{ checked }}</label>

<input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
<label for="jack">Jack</label>
<input type="checkbox" id="john" value="John" v-model="checkedNames">
<label for="john">John</label>
<input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
<label for="mike">Mike</label>
<br>
<span>Checked names: {{ checkedNames }}</span>

new Vue({
  el: '...',
  data: {
    checkedNames: []
  }
})

<!--Radio-->
<input type="radio" id="one" value="One" v-model="picked">
<label for="one">One</label>
<br>
<input type="radio" id="two" value="Two" v-model="picked">
<label for="two">Two</label>
<br>
<span>Picked: {{ picked }}</span>

<!--Select-->
<select v-model="selected">
  <option disabled value="">Please select one</option>
  <option>A</option>
  <option>B</option>
  <option>C</option>
</select>
<span>Selected: {{ selected }}</span>

new Vue({
  el: '...',
  data: {
    selected: ''
  }
})
//multile select (bound to Array)
<select v-model="selected" multiple>
  <option>A</option>
  <option>B</option>
  <option>C</option>
</select>
<br>
<span>Selected: {{ selected }}</span>

//v-for
<select v-model="selected">
  <option v-for="option in options" v-bind:value="option.value">
    {{ option.text }}
  </option>
</select>
<span>Selected: {{ selected }}</span>

new Vue({
  el: '...',
  data: {
    selected: 'A',
    options: [
      { text: 'One', value: 'A' },
      { text: 'Two', value: 'B' },
      { text: 'Three', value: 'C' }
    ]
  }
})


<!--Value Bindings: v-bind for dynamic property-->
<input
  type="checkbox"
  v-model="toggle"
  true-value="yes"
  false-value="no"
>
// when checked:
vm.toggle === 'yes'
// when unchecked:
vm.toggle === 'no'

<input type="radio" v-model="pick" v-bind:value="a">
// when checked:
vm.pick === vm.a

<select v-model="selected">
  <!-- inline object literal -->
  <option v-bind:value="{ number: 123 }">123</option>
</select>
// when selected:
typeof vm.selected // => 'object'
vm.selected.number // => 123

<!--Modifiers-->
.lazy, .number, .trim

//Vue components allow you to build reusable inputs with completely customized behavior. 
//These inputs even work with v-model