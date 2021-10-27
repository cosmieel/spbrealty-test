<template>
  <cards-actions />
  <cards-list />
</template>

<script>
import CardsList from "@/components/CardsList.vue";
import CardsActions from "@/components/CardsActions.vue";

export default {
  name: "cart-body",
  components: {
    CardsList,
    CardsActions,
  },
};
</script>

<style lang="scss" scoped></style>
