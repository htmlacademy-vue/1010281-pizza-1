<template>
  <div class="sheet">
    <h2 class="title title--small sheet__title">Выберите размер</h2>
    <div class="sheet__content diameter">
      <SelectorItem
        v-for="size in sizes"
        :key="size.id"
        class="diameter__input"
        :class="setSizeLabelClass(size.multiplier)"
        :type="size"
        name="diameter"
        :value="size.name"
        :checked="size.multiplier === 2"
      >
        <span>{{ size.name }}</span>
      </SelectorItem>
    </div>
  </div>
</template>

<script>
import SelectorItem from "@/common/components/SelectorItem.vue";

export default {
  name: "BuilderSizeSelector",

  components: {
    SelectorItem,
  },

  props: {
    sizes: {
      type: Array,
      required: true,
    },
  },

  methods: {
    setSizeLabelClass(multiplier) {
      const multipliers = {
        1: "small",
        2: "normal",
        3: "big",
      };
      return `diameter__input--${multipliers[multiplier]}`;
    },
  },
};
</script>
