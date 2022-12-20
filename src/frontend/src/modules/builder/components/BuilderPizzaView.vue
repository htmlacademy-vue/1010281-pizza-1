<template>
  <div class="content__constructor">
    <AppDrop @drop="add">
      <div class="pizza pizza--foundation--big-tomato">
        <div class="pizza__wrapper"></div>
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

  data() {
    return {
      ingredientsTranslate,
    };
  },

  methods: {
    add(ingredient) {
      const div = document.createElement("div");
      div.classList.add("pizza__filling");
      div.classList.add(
        `pizza__filling--${this.ingredientsTranslate[ingredient.name]}`
      );
      document.querySelector(".pizza__wrapper").appendChild(div);
    },
  },
};
</script>
