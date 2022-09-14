<template>
  <div>
    <AppLayout />
    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>
          <div class="content__dough">
            <BuilderDoughSelector :dough="dough" />
          </div>
          <div class="content__diameter">
            <BuilderSizeSelector :sizes="sizes" />
          </div>
          <div class="content__ingredients">
            <div class="sheet">
              <h2 class="title title--small sheet__title">
                Выберите ингредиенты
              </h2>
              <div class="sheet__content ingredients">
                <div class="ingredients__sauce">
                  <p>Основной соус:</p>
                  <RadioButton
                    v-for="sauce in sauces"
                    :key="sauce.id"
                    name="sauce"
                    :value="sauce.name"
                    :checked="sauce.id === 1"
                    class="ingredients__input"
                  >
                    <span>{{ sauce.name }}</span>
                  </RadioButton>
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
          </div>
          <div class="content__pizza">
            <label class="input">
              <span class="visually-hidden">Название пиццы</span>
              <input
                type="text"
                name="pizza_name"
                placeholder="Введите название пиццы"
              />
            </label>
            <div class="content__constructor">
              <div class="pizza pizza--foundation--big-tomato">
                <div class="pizza__wrapper">
                  <div class="pizza__filling pizza__filling--ananas"></div>
                  <div class="pizza__filling pizza__filling--bacon"></div>
                  <div class="pizza__filling pizza__filling--cheddar"></div>
                </div>
              </div>
            </div>

            <div class="content__result">
              <p>Итого: 0 ₽</p>
              <button type="button" class="button" disabled>Готовьте!</button>
            </div>
          </div>
        </div>
      </form>
    </main>
  </div>
</template>

<script>
import pizza from "@/static/pizza.json";
import AppLayout from "@/layouts/AppLayout.vue";
import RadioButton from "@/common/components/RadioButton.vue";
import ItemCounter from "@/common/components/ItemCounter.vue";
import BuilderDoughSelector from "@/modules/builder/components/BuilderDoughSelector.vue";
import BuilderSizeSelector from "@/modules/builder/components/BuilderSizeSelector.vue";

export default {
  name: "Index",

  components: {
    AppLayout,
    RadioButton,
    ItemCounter,
    BuilderDoughSelector,
    BuilderSizeSelector,
  },

  data() {
    return {
      ingredients: pizza.ingredients,
      sauces: pizza.sauces,
      sizes: pizza.sizes,
      dough: pizza.dough,
    };
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

<style lang="scss" scoped></style>
