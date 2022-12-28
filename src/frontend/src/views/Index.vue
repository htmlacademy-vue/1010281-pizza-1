<template>
  <div>
    <AppLayout />
    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>
          <BuilderDoughSelector
            :dough="dough"
            @change-dough-size="changeDoughSize"
          />
          <BuilderSizeSelector :sizes="sizes" />
          <BuilderIngredientsSelector
            :ingredients="ingredients"
            :sauces="sauces"
            @change="changeSauce"
            @update-ingredients="updateIngredients"
          />
          <div class="content__pizza">
            <label class="input">
              <span class="visually-hidden">Название пиццы</span>
              <input
                type="text"
                name="pizza_name"
                placeholder="Введите название пиццы"
              />
            </label>
            <BuilderPizzaView
              :sauce="selectedSauce"
              :selectedIngredients="selectedIngredients"
              :doughSize="selectedDoughSize"
            />
            <BuilderPriceCounter />
          </div>
        </div>
      </form>
    </main>
  </div>
</template>

<script>
import pizza from "@/static/pizza.json";
import AppLayout from "@/layouts/AppLayout.vue";
import BuilderDoughSelector from "@/modules/builder/components/BuilderDoughSelector.vue";
import BuilderSizeSelector from "@/modules/builder/components/BuilderSizeSelector.vue";
import BuilderIngredientsSelector from "@/modules/builder/components/BuilderIngredientsSelector.vue";
import BuilderPizzaView from "@/modules/builder/components/BuilderPizzaView.vue";
import BuilderPriceCounter from "../modules/builder/components/BuilderPriceCounter.vue";

export default {
  name: "Index",

  components: {
    AppLayout,
    BuilderDoughSelector,
    BuilderSizeSelector,
    BuilderIngredientsSelector,
    BuilderPizzaView,
    BuilderPriceCounter,
  },

  data() {
    return {
      ingredients: pizza.ingredients,
      sauces: pizza.sauces,
      sizes: pizza.sizes,
      dough: pizza.dough,

      selectedSauce: "tomato",
      selectedIngredients: [],
      selectedDoughSize: "small",
    };
  },

  methods: {
    changeSauce(sauce) {
      this.selectedSauce = sauce;
    },
    updateIngredients(ingredients) {
      this.selectedIngredients = ingredients;
    },
    changeDoughSize(size) {
      this.selectedDoughSize = size === "light" ? "small" : "big";
    },
  },
};
</script>

<style lang="scss" scoped></style>
