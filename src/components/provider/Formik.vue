<script setup>
import { ref, provide } from "vue";
import { data as dataKey } from "./DataProviderKeys";
const data = ref();

const $emit = defineEmits(["submitFinal"]);

const props = defineProps({
  validate: {
    type: Function,
    required: true,
  },
  initialValues: {
    type: Object,
    required: true,
  },
});

data.value = props.initialValues;

const handleSubmit = () => {
  const errors = props.validate(data.value);

  if (Object.keys(errors).length === 0) $emit("submitFinal", data.value);
};

provide(dataKey, data);
</script>

<template>
  <slot :handleSubmit="handleSubmit"></slot>
</template>
