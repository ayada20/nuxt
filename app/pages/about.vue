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
const isButtonDisabled = ref(false);
const seen = true;
function doSomething() {
  alert("hola");
  isButtonDisabled.value = false;
}
</script>

<template>
  <h1>1.Template Syntax</h1>
  <h2>Text Interpolation</h2>
  <p>
    Mensaje:
    {{
      "Mustache Syntax - > double curly braces, as we see, directives are pre-fixedwith v-, so we can say that they are special attributes provided by VUe "
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
  <button v-bind:disabled="isButtonDisabled" @click="doSomething">
    Button
  </button>

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
  <h1>8.Refs:</h1>
  <p>
    With the.value property we can detect when a ref has been accesed or
    mutated, Vue preforms the tracking in the egetter and performs it in its
    setter. we van pass refs to functions too when renting access to the latest
    value and the reactivity connection. In conclsion we can say that recativity
    allows us to adjust changes in a declarative manner. Refs can hold deep
    nested objects, arrays, JS(map). - nextTick() global API : it ensures that
    each component updates only once no matter the times of changes we've made.
    Types: - reactive() : - computed() : - event Handlers like
    handleChange(event) : -provide / inject : - component Emits :
  </p>

  <h1>9. Props :</h1>
  1.
  <P>
    runtime declaration: declaracion en tiempo de ejecución, pasas un objeto con
    tipos y opcioones. si es obligatorio va entre llaves: const
    props=defineProps({ name:{type:String, required:true}, creo¿? age: Number }) </P
  >2.
  <P
    >Type-based declaration(Declaración basada en tipos): const
    props=defineProps<{ name:string --> obligatorio por defecto. age?: number
    --> opcional(?) }>().
  </P>
  3.
  <P>
    Usando una interfaz separada(Interface): interface Props{ name: string
    age?:number } const props = defineProps < Props>() -->USA EL MOLDE
    console.log(props.name) </P
  >4.
  <P>
    importando tipos de otrso archivos: import type {Props} from './props.ts'
    const props = efineProps < Props>() </P
  >5.
  <P>
    <h3>Valores por defecto: Props Default Values:</h3>
    <p>
      -->Reactive props destructure:extrae props y asigna defaults por defecto.
    </p>
    <p>-->withDefaults(Marco para Defaults): verifica tipos y quita '?'.</p>
    <p>
      -->Sin < script setup>: usa defineComponents() para inferir tipos de
      props.
    </p>
    <p>-->Tipos complejos para props (complex prop types):con type-based</p>
    <p>-->usa interfaces para objetos y con runtime</p>
    <p>-->usa PropType</p></P
  >
  <p>6. Typing Component Emits(como tipar eventos que emite un componente)</p>
  <p>a)con < script setup>:</p>
  <p>
    -->RUNTIME DECLARATION < script setup lang="ts"> const emit =
    defineEmits(['change', 'update']) // Solo nombres de eventos emit('change',
    123) // OK < / script >
  </p>
  <p>-->OPTION BASED (CON VALIDACION)</p>
  <p>-->TYPE-BASED(MAS PRECISA)</p>
  <p>b)sin < script setup >:</p>

  <p></p>

  <p>10.Typing ref() Cónmo tipar refs:</p>
  <p>10.Typing reactive() Cónmo tipar reactive:</p>
  <p>10.Typing computed() Cónmo tipar computed:</p>
  <p>10.Typing event Handlers() Cónmo tipar manejadores de eventos:</p>
  -->Sin tipo (malo): -->Con tipo (bueno):
</template>
