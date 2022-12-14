<script setup>
import { provide, reactive } from "vue";
import { data as dataKey } from "./DataProviderKeys";
import { error as errorKey } from "./ErrorProviderKeys";

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

const errors = reactive({ value: null });

const handleSubmit = () => {
  const validate = props.validate(data);
  errors.value = validate;

  const errorValidate = validate;

  if (Object.keys(errorValidate).length === 0) $emit("submitFinal", data);
};

provide(dataKey, data);
provide(errorKey, errors);
</script>

<template>
  <slot :handleSubmit="handleSubmit"></slot>
</template>
