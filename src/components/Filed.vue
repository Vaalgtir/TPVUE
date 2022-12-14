<script setup>
import { inject } from "vue";
import { data as dataKey } from "./provider/DataProviderKeys";

const props = defineProps(["name"]);

const data = inject(dataKey);

const value = data[props.name];
</script>

<template>
  <input value="{{value}}" />
</template>
