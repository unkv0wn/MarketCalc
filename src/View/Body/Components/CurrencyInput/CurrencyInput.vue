<script setup>
import { useCurrencyInput } from 'vue-currency-input';

const props = defineProps({
  modelValue: {
    type: Number,
    default: 0
  },
  options: {
    type: Object,
    default: undefined
  },
  customInstance: {
    type: Object,
    default: undefined
  }
});
defineEmits(['change', 'update:modelValue']);

const { inputRef, numberValue } = props.customInstance? props.customInstance : useCurrencyInput(props.options);
</script>

<template>
  <input
    ref="inputRef"
    type="text"
    @input="$emit('change', numberValue)"
    :value="modelValue"
  />
</template>