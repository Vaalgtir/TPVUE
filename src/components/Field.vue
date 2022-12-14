<script setup>
import { computed } from "@vue/reactivity";
import { inject, watch } from "vue";
import { data as dataKey } from "./provider/DataProviderKeys";
import { error as errorKey } from "./provider/ErrorProviderKeys";

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  as: {
    type: String,
    required: true,
    default: "input",
  },
});

const dataValue = inject(dataKey);
const errorValue = inject(errorKey);

let currentError = errorValue?.value && errorValue?.value[props.name];

const value = dataValue[props.name];

const handleChange = (event) => {
  dataValue[props.name] = event.target.value;
};

watch(errorValue, () => {
  currentError = errorValue?.value && errorValue?.value[props.name];
  console.log("here", currentError);
});
</script>

<template>
  <!-- <input :value="value" @input="handleChange" /> -->
  {{ currentError }}
  <component v-bind:is="as" :value="value" @input="handleChange"></component>
  <div v-show="currentError">{{ currentError }}</div>
</template>
