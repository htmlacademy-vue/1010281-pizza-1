<template>
  <div>
    <header class="header">
      <div class="header__logo">
        <a href="index.html" class="logo">
          <img :src="logo" alt="V!U!E! Pizza logo" width="90" height="40" />
        </a>
      </div>
      <div class="header__cart">
        <a href="cart.html">0 ₽</a>
      </div>
      <div class="header__user">
        <a href="#" class="header__login"><span>Войти</span></a>
      </div>
    </header>
    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>
          <div class="content__dough">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите тесто</h2>
              <div class="sheet__content dough">
                <label
                  v-for="doughType in dough"
                  :key="doughType.id"
                  class="dough__input"
                  :class="setDougLabelClass(doughType.name)"
                >
                  <input
                    type="radio"
                    name="dought"
                    :value="doughType.name"
                    class="visually-hidden"
                    :checked="doughType.id === 1"
                  />
                  <b>{{ doughType.name }}</b>
                  <span>{{ doughType.description }}</span>
                </label>
              </div>
            </div>
          </div>
          <div class="content__diameter">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите размер</h2>
              <div class="sheet__content diameter">
                <label
                  v-for="size in sizes"
                  :key="size.id"
                  class="diameter__input"
                  :class="setSizeLabelClass(size.multiplier)"
                >
                  <input
                    type="radio"
                    name="diameter"
                    :value="size.name"
                    class="visually-hidden"
                    :checked="size.multiplier === 2"
                  />
                  <span>{{ size.name }}</span>
                </label>
              </div>
            </div>
          </div>
          <div class="content__ingredients">
            <div class="sheet">
              <h2 class="title title--small sheet__title">
                Выберите ингредиенты
              </h2>
              <div class="sheet__content ingredients">
                <div class="ingredients__sauce">
                  <p>Основной соус:</p>
                  <label
                    v-for="sauce in sauces"
                    :key="sauce.id"
                    class="radio ingredients__input"
                  >
                    <input
                      type="radio"
                      name="sauce"
                      :value="sauce.name"
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
                      <span
                        class="filling"
                        :class="setFillingLabelClass(ingredient.name)"
                      >
                        {{ ingredient.name }}
                      </span>
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
import logo from "@/assets/img/logo.svg";
import pizza from "@/static/pizza.json";

export default {
  name: "Index",

  data() {
    return {
      logo,
      ingredients: pizza.ingredients,
      sauces: pizza.sauces,
      sizes: pizza.sizes,
      dough: pizza.dough,
    };
  },

  methods: {
    setDougLabelClass(type) {
      const doughs = {
        Толстое: "large",
        Тонкое: "light",
      };
      return `dough__input--${doughs[type]}`;
    },
    setSizeLabelClass(multiplier) {
      const multipliers = {
        1: "small",
        2: "normal",
        3: "big",
      };
      return `diameter__input--${multipliers[multiplier]}`;
    },
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
