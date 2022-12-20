<template>
  <div class="content__ingredients">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите ингредиенты</h2>
      <div class="sheet__content ingredients">
        <div class="ingredients__sauce">
          <p>Основной соус:</p>
          <label
            class="radio ingredients__input"
            v-for="sauce in sauces"
            :key="sauce.id"
          >
            <input
              type="radio"
              name="sauce"
              :value="selectSauceType(sauce.name)"
              :checked="sauce.id === 1"
            />
            <span>{{ sauce.name }}</span>
          </label>
        </div>
        <div class="ingredients__filling">
          <p>Начинка:</p>
          <ul class="ingredients__list">
            <li
              v-for="ingredient in ingredients"
              :key="ingredient.id"
              class="ingredients__item"
            >
              <AppDrag :transferData="ingredient">
                <span
                  class="filling"
                  :class="`filling--${selectFillingType(ingredient.name)}`"
                >
                  {{ ingredient.name }}
                </span>
              </AppDrag>
              <div class="counter counter--orange ingredients__counter">
                <button
                  type="button"
                  class="counter__button counter__button--minus"
                  disabled
                >
                  <span class="visually-hidden">Меньше</span>
                </button>
                <input
                  type="text"
                  name="counter"
                  class="counter__input"
                  value="0"
                />
                <button
                  type="button"
                  class="counter__button counter__button--plus"
                >
                  <span class="visually-hidden">Больше</span>
                </button>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AppDrag from "@/common/components/AppDrag.vue";
import { ingredientsTranslate } from "@/common/constants.js";

export default {
  name: "BuilderIngredientsSelector",

  components: {
    AppDrag,
  },

  props: {
    ingredients: {
      type: Array,
      required: true,
    },
    sauces: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      ingredientsTranslate,
    };
  },

  methods: {
    selectFillingType(name) {
      return this.ingredientsTranslate[name];
    },

    selectSauceType(name) {
      const sauces = {
        Томатный: "tomato",
        Сливочный: "creamy",
      };
      return sauces[name];
    },
  },
};
</script>
