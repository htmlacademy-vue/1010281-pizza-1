<template>
  <div class="content__dough">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите тесто</h2>
      <div class="sheet__content dough">
        <label
          v-for="doughItem in dough"
          :key="doughItem.id"
          class="dough__input"
          :class="`dough__input--${selectDoughType(doughItem.name)}`"
        >
          <input
            type="radio"
            name="dought"
            :value="selectDoughType(doughItem.name)"
            class="visually-hidden"
            :checked="doughItem.id === 1"
          />
          <b>{{ doughItem.name }}</b>
          <span>{{ doughItem.description }}</span>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BuilderDoughSelector",

  props: {
    dough: {
      type: Array,
      required: true,
    },
  },

  methods: {
    selectDoughType(type) {
      const doughs = {
        Толстое: "large",
        Тонкое: "light",
      };
      return doughs[type];
    },
  },
};
</script>
