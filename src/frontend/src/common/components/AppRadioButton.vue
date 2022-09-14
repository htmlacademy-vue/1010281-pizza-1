<template>
  <label class="radio">
    <input type="radio" :name="name" :value="value" :checked="checked" />
    <slot></slot>
  </label>
</template>

<script>
export default {
  name: "RadioButton",

  props: {
    name: {
      type: String,
      required: true,
    },
    value: {
      type: [String, Number],
      required: true,
    },
    checked: {
      type: Boolean,
      default: false,
    },
  },
};
</script>
