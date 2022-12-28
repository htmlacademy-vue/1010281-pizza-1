<template>
  <div class="content__diameter">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите размер</h2>
      <div class="sheet__content diameter">
        <label
          v-for="size in sizes"
          :key="size.id"
          class="diameter__input"
          :class="`diameter__input--${selectSizeMultiplier(size.multiplier)}`"
        >
          <input
            type="radio"
            name="diameter"
            :value="selectSizeMultiplier(size.multiplier)"
            class="visually-hidden"
            :checked="size.multiplier === 2"
          />
          <span>{{ size.name }}</span>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BuilderSizeSelector",

  props: {
    sizes: {
      type: Array,
      required: true,
    },
  },

  methods: {
    selectSizeMultiplier(multiplier) {
      const multipliers = {
        1: "small",
        2: "normal",
        3: "big",
      };
      return multipliers[multiplier];
    },
  },
};
</script>
