<template>
  <div class="content__constructor">
    <div :class="`pizza pizza--foundation--big-${sauce}`">
      <div class="pizza__wrapper">
        <div
          v-for="ingredient in selectedIngredients"
          :class="`pizza__filling pizza__filling--${ingredient}`"
          :key="ingredient"
        ></div>
      </div>
    </div>
  </div>
</template>

<script>
import { ingredientsTranslate } from "@/common/constants.js";

export default {
  name: "BuilderPizzaView",

  props: {
    sauce: {
      type: String,
      required: true,
    },
  },

  data() {
    return {
      ingredientsTranslate,
      ingredients: [],
    };
  },

  methods: {
    add(ingredient) {
      this.ingredients.push(this.ingredientsTranslate[ingredient.name]);
    },
  },
};
</script>
