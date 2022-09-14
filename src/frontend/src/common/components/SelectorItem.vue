<template>
  <label>
    <input
      type="radio"
      :name="name"
      :value="value"
      class="visually-hidden"
      :checked="checked"
    />
    <slot></slot>
  </label>
</template>

<script>
export default {
  name: "SelectorItem",

  props: {
    type: {
      type: Object,
      required: true,
    },
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
      required: false,
    },
  },
};
</script>
