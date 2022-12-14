<script setup>
import { inject } from "vue";
import { data as dataKey } from "./provider/DataProviderKeys";

const props = defineProps(["name"]);

const data = inject(dataKey);

const value = data[props.name];

const handleChange = (event) => {
  console.log(event.target.value);
};
</script>

<template>
  <input :value="value" @change="handleChange" />
</template>
