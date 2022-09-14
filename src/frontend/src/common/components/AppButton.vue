<template>
  <button v-bind="$attrs" class="button"><slot></slot></button>
</template>

<script>
export default {
  name: "AppButton",
};
</script>
