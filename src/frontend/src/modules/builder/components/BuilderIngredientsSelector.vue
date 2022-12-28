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
              @change="changeSauce"
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
              <span
                class="filling"
                :class="`filling--${selectFillingType(ingredient.name)}`"
              >
                {{ ingredient.name }}
              </span>
              <div class="counter counter--orange ingredients__counter">
                <button
                  type="button"
                  class="counter__button counter__button--minus"
                  @click="removeIngredient(selectFillingType(ingredient.name))"
                  :disabled="
                    ingredientsCount[selectFillingType(ingredient.name)] === 0
                  "
                >
                  <span class="visually-hidden">Меньше</span>
                </button>
                <input
                  type="text"
                  name="counter"
                  class="counter__input"
                  v-model.number="
                    ingredientsCount[selectFillingType(ingredient.name)]
                  "
                />
                <button
                  type="button"
                  class="counter__button counter__button--plus"
                  @click="addIngredient(selectFillingType(ingredient.name))"
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
import { ingredientsTranslate } from "@/common/constants.js";

export default {
  name: "BuilderIngredientsSelector",

  emits: ["update-ingredients"],

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
      ingredientsCount: {
        mushrooms: 0,
        tomatoes: 0,
        ananas: 0,
        bacon: 0,
        blue_cheese: 0,
        cheddar: 0,
        chile: 0,
        ham: 0,
        jalapeno: 0,
        mozzarella: 0,
        olives: 0,
        onion: 0,
        parmesan: 0,
        salami: 0,
        salmon: 0,
      },
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

    changeSauce(event) {
      this.$emit("change", event.target.value);
    },

    addIngredient(ingredient) {
      this.ingredientsCount[ingredient] += 1;
      this.passIngredients();
    },

    removeIngredient(ingredient) {
      this.ingredientsCount[ingredient] -= 1;
      this.passIngredients();
    },

    passIngredients() {
      const selectedIngredients = Object.keys(this.ingredientsCount).filter(
        (ingredient) => this.ingredientsCount[ingredient]
      );
      this.$emit("update-ingredients", selectedIngredients);
    },
  },
};
</script>
