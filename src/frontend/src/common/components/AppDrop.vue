<template>
  <div @drop.stop="onDrop" @dragover.prevent @dragenter.prevent>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "AppDrop",

  methods: {
    onDrop({ dataTransfer }) {
      const payload = dataTransfer.getData("transfer");
      if (payload) {
        const transferData = JSON.parse(dataTransfer.getData("transfer"));
        this.$emit("drop", transferData);
      }
    },
  },
};
</script>
