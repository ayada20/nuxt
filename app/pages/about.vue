<script lang="ts" setup>
import { ref } from "vue";
const count = ref(0);
count.value++;
console.log(count);

const message = ref(
  "this is Mustache syntax(double curly braces with v-html directive)"
);
const messageVhtml = ref(
  "this is Mustache syntax(double curly braces with v-html directive)"
);

const objetOfAttrributes = {
  id: "container",
  class: "wrapper",
  style: "background-color:grey",
};
const isButtonDisabled = true;
const seen = true;
function doSomething() {
  alert("hola");
}
</script>

<template>
  <h1>1.Template Syntax</h1>
  <h2>Text Interpolation</h2>
  <p>
    Mensaje:
    {{
      "Mustache Syntax - > double curly braces, , as we see, directives are pre-fixedwith v-, so we can say that they are special attributes provided by VUe "
    }}
  </p>
  <br />
  <h1>2.Raw HTML</h1>

  <h4>Using text interpolation: {{ message }}</h4>
  <h4>Using v-html directive: <span v-html="messageVhtml"></span></h4>
  <br />
  <p style="color: red">This should be red, using interpolation</p>
  <br />
  <h1>3.Attribute Bindings V-bind with multiple attributes</h1>
  <p>
    V-bind instructs Vue to keep the attributes id's in sync with component's
    dynamic property. <br />
    the attribute will be removed if from the rendered element if the bound
    value is null or undefined.
    <br />
    V-bind shorted(optional) syntax exaple: V-bind:id --> :id.
  </p>
  <h4 v-bind="objetOfAttrributes">
    As we can't use Mustaches in HTML we should use v-bind directive
  </h4>
  <h1>4.Boolean Attributes</h1>
  <p>
    As we know, noolean attributes are attributes that indicate true or false
    values for example: disabled attribute. In the next example
  </p>
  <button v-bind:disabled="isButtonDisabled">Button</button>

  <h1>5.Using JavaScript Expressions</h1>

  <h1>6.Directives</h1>
  <h4>
    v-prefix attributes (v-html, v-bind...), it updates when the valor its
    changed
  </h4>
  <p v-if="seen">Now you see me because the variable seen is true</p>

  <!-- tema 2 Reactivity funcamentals -->
  <h1>7.Declaring Reactive State</h1>

  <ul>
    <li>
      setup() : if we want to access a ref component, we must declare them from
      a components setup() function.
    </li>

    <li>
      ref() : the ref() function takes the argument and returns it wrapped (ref
      object with .value property).
    </li>
    <li>
      reactive () : Typing reactive (recative() ) infers the type of its
      argument(it is recomendable NOT usung it).
    </li>
    <li>
      computed() : this infers its type based on the getter's return value.
    </li>
    <p>Counter message: {{ count }}</p>
  </ul>
  <a @click="doSomething"> Buenos dias. </a>
  <button @click="count++">
    {{ count }}
  </button>
</template>
