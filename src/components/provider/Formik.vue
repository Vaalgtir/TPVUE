<script setup>
import { provide, reactive } from "vue";
import { data as dataKey } from "./DataProviderKeys";

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
const data = reactive(props.initialValues);

const handleSubmit = () => {
  const errors = props.validate(data);

  if (Object.keys(errors).length === 0) $emit("submitFinal", data);
};

provide(dataKey, data);
</script>

<template>
  <slot :handleSubmit="handleSubmit"></slot>
</template>
