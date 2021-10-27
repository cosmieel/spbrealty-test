<template>
  <div class="cart-header">
    <form action="" class="cart-header__form">
      <div class="cart-header__search">
        <icon-search class="cart-header__search-icon" />
        <input
          type="text"
          class="cart-header__search-input"
          v-model="searchQuery"
          placeholder="Введите ЖК / корпус / № квартиры / № паркинга"
        />
      </div>
    </form>
    <div class="cart-header__status">
      <status-list />
    </div>
    <div class="cart-header__clear">
      <base-button :buttonText="buttonText.clear"><icon-clear /></base-button>
    </div>
  </div>
</template>

<script>
import IconSearch from "@/components/icons/IconSearch.vue";
import IconClear from "@/components/icons/IconClear.vue";
import StatusList from "@/components/StatusList.vue";

export default {
  name: "cart-header",
  components: {
    IconSearch,
    IconClear,
    StatusList,
  },
  data() {
    return {
      searchQuery: "",
      buttonText: {
        clear: "Очистить корзину",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
.cart-header {
  display: flex;
  padding-bottom: 32px;

  &__form {
    padding-right: 10px;
    width: 100%;
    max-width: 637px;
  }
  &__search {
    position: relative;
  }
  &__search-icon {
    position: absolute;
    top: 7px;
    left: 7px;
  }
  &__search-input {
    border: 1px solid #c4c4c4;
    padding: 10px 45px 9px;
    background: transparent;
    width: 100%;
    height: 38px;
    outline: none;
    transition: border-color 0.1s ease-out;

    &::placeholder {
      color: #9b9b9b;
      transition: opacity 0.1s ease-out;
    }

    &:focus {
      border-color: #000;

      &::placeholder {
        opacity: 0.5;
      }
    }
  }

  &__status {
    padding-right: 10px;
  }
}
</style>
