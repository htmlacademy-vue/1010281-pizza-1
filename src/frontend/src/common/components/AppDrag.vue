<template>
  <div
    draggable="true"
    @dragstart.self="onDrag"
    @dragover.prevent
    @dragenter.prevent
  >
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "AppDrag",

  props: {
    transferData: {
      type: Object,
      required: true,
    },
  },

  methods: {
    onDrag({ dataTransfer }) {
      dataTransfer.effectAllowed = "move";
      dataTransfer.dropEffect = "move";
      dataTransfer.setData("transfer", JSON.stringify(this.transferData));
    },
  },
};
</script>
