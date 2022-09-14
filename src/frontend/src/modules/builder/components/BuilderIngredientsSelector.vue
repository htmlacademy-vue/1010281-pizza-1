<template>
  <div class="sheet">
    <h2 class="title title--small sheet__title">Выберите ингредиенты</h2>
    <div class="sheet__content ingredients">
      <div class="ingredients__sauce">
        <p>Основной соус:</p>
        <AppRadioButton
          v-for="sauce in sauces"
          :key="sauce.id"
          name="sauce"
          :value="sauce.name"
          :checked="sauce.id === 1"
          class="ingredients__input"
        >
          <span>{{ sauce.name }}</span>
        </AppRadioButton>
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
              :class="setFillingLabelClass(ingredient.name)"
            >
              {{ ingredient.name }}
            </span>
            <ItemCounter class="ingredients__counter" />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import AppRadioButton from "@/common/components/AppRadioButton.vue";
import ItemCounter from "@/common/components/ItemCounter.vue";

export default {
  name: "BuilderIngredientsSelector",

  components: {
    AppRadioButton,
    ItemCounter,
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

  methods: {
    setFillingLabelClass(name) {
      const ingredients = {
        Грибы: "mushrooms",
        Томаты: "tomatoes",
        Ананас: "ananas",
        Бекон: "bacon",
        "Блю чиз": "blue_cheese",
        Чеддер: "cheddar",
        Чили: "chile",
        Ветчина: "ham",
        Халапеньо: "jalapeno",
        Моцарелла: "mozzarella",
        Маслины: "olives",
        Лук: "onion",
        Пармезан: "parmesan",
        Салями: "salami",
        Лосось: "salmon",
      };
      return `filling--${ingredients[name]}`;
    },
  },
};
</script>
