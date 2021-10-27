<template>
  <div class="cards-actions">
    <div class="cards-actions__checkbox">
      <base-checkbox :withText="true" v-model="isCheckedAll">
        Все
      </base-checkbox>
    </div>
    <div class="cards-actions__button">
      <base-button :buttonText="buttonText.save"><icon-save /></base-button>
    </div>
    <div class="cards-actions__button">
      <base-button :buttonText="buttonText.send"><icon-send /></base-button>
    </div>
    <div class="cards-actions__button">
      <base-button :buttonText="buttonText.delete"><icon-bin /></base-button>
    </div>
  </div>
</template>

<script>
import IconSave from "@/components/icons/IconSave.vue";
import IconSend from "@/components/icons/IconSend.vue";
import IconBin from "@/components/icons/IconBin.vue";

export default {
  name: "cards-actions",
  components: {
    IconSave,
    IconSend,
    IconBin,
  },
  data() {
    return {
      buttonText: {
        save: "Сохранить",
        send: "Отправить",
        delete: "Удалить",
      },
      isCheckedAll: false,
    };
  },
};
</script>

<style lang="scss" scoped>
.cards-actions {
  padding-left: 25px;
  display: flex;
  align-items: center;
  padding-bottom: 20px;

  &__checkbox {
    padding-right: 3px;

    .base-checkbox__text {
      padding-left: 10px;
    }
  }

  &__button {
    padding-left: 10px;
  }
}
</style>
