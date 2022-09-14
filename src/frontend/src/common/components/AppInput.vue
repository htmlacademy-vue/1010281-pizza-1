<template>
  <label class="input">
    <slot></slot>
    <input :type="type" :name="name" :placeholder="placeholder" />
  </label>
</template>

<script>
export default {
  name: "AppInput",

  props: {
    type: {
      type: String,
      default: "text",
    },
    name: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      default: "",
    },
  },
};
</script>
