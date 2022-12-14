<script setup>
const $emit = defineEmits(["submitFinal"]);
const props = defineProps({
  validate: {
    type: Function,
    required: true,
  },
});

const handleSubmit = () => {
  $emit("submitFinal", "wdrjhkfgqze ");
};
</script>

<template>
  <slot :handleSubmit="handleSubmit"></slot>
</template>
