<script setup>
import { inject } from "vue";
import { data as dataKey } from "./provider/DataProviderKeys";

const props = defineProps(["name"]);

const dataValue = inject(dataKey);

const value = dataValue[props.name];

const handleChange = (event) => {
  dataValue[props.name] = event.target.value;
};

const options = [
  {
    name: "zefze",
    component: {
      template: "<div>sd;jhgksu</div>",
    },
  },
  {
    name: "input",
    component: {
      template: "<div>hcgsduygc</div>",
    },
  },
];

const currentOption =
  options.find((opt) => opt.name === props.name) ||
  options.find((opt) => opt.name === "input");

console.log(currentOption);
</script>

<template>
  <!-- <input :value="value" @input="handleChange" /> -->
  <!-- {{ currentOption.component }} -->
  <component
    v-bind:is="currentOption.component"
    :value="value"
    @input="handleChange"
  ></component>
</template>
