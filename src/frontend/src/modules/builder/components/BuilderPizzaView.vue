<template>
  <div class="content__constructor">
    <AppDrop @drop="add">
      <div :class="`pizza pizza--foundation--big-${sauce}`">
        <div class="pizza__wrapper">
          <div
            v-for="ingredient in ingredients"
            :class="`pizza__filling pizza__filling--${ingredient}`"
            :key="ingredient"
          ></div>
        </div>
      </div>
    </AppDrop>
  </div>
</template>

<script>
import AppDrop from "@/common/components/AppDrop.vue";
import { ingredientsTranslate } from "@/common/constants.js";

export default {
  name: "BuilderPizzaView",

  components: { AppDrop },

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
