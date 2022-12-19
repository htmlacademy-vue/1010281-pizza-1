<template>
  <div class="content__result">
    <p>Итого: 0 ₽</p>
    <AppButton type="button" disabled>Готовьте!</AppButton>
  </div>
</template>

<script>
import AppButton from "@/common/components/AppButton.vue";

export default {
  name: "BuilderPriceCounter",

  components: {
    AppButton,
  },
};
</script>
