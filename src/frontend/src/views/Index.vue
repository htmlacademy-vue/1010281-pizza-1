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
            <BuilderIngredientsSelector
              :ingredients="ingredients"
              :sauces="sauces"
            />
          </div>
          <div class="content__pizza">
            <AppInput
              type="text"
              name="pizza_name"
              placeholder="Введите название пиццы"
            >
              <span class="visually-hidden">Название пиццы</span>
            </AppInput>
            <BuilderPizzaView />
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
import AppInput from "@/common/components/AppInput.vue";
import BuilderPriceCounter from "@/common/components/BuilderPriceCounter.vue";

export default {
  name: "Index",

  components: {
    AppLayout,
    BuilderDoughSelector,
    BuilderSizeSelector,
    BuilderIngredientsSelector,
    BuilderPizzaView,
    AppInput,
    BuilderPriceCounter,
  },

  data() {
    return {
      ingredients: pizza.ingredients,
      sauces: pizza.sauces,
      sizes: pizza.sizes,
      dough: pizza.dough,
    };
  },
};
</script>

<style lang="scss" scoped></style>
