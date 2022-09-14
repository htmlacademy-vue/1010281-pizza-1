<template>
  <div class="sheet">
    <h2 class="title title--small sheet__title">Выберите тесто</h2>
    <div class="sheet__content dough">
      <SelectorItem
        v-for="doughType in dough"
        :key="doughType.id"
        class="dough__input"
        :class="setDougLabelClass(doughType.name)"
        :type="doughType"
        name="dough"
        :value="doughType.name"
        :checked="doughType.id === 1"
      >
        <b>{{ doughType.name }}</b>
        <span>{{ doughType.description }}</span>
      </SelectorItem>
    </div>
  </div>
</template>

<script>
import SelectorItem from "@/common/components/SelectorItem.vue";

export default {
  name: "BuilderDoughSelector",

  components: {
    SelectorItem,
  },

  props: {
    dough: {
      type: Array,
      required: true,
    },
  },

  methods: {
    setDougLabelClass(type) {
      const doughs = {
        Толстое: "large",
        Тонкое: "light",
      };
      return `dough__input--${doughs[type]}`;
    },
  },
};
</script>
