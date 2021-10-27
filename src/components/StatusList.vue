<template>
  <div class="status-list">
    <div class="status-list__toggle" @click="showStatusList">
      <span>Все статусы</span>
      <icon-dropdown
        class="status-list__icon"
        :class="{ '_is-active': isVisible }"
      />
    </div>
    <div class="status-list__popover" :class="{ '_is-visible': isVisible }">
      <base-checkbox
        class="status-list__checkbox"
        :withText="true"
        v-model="isCheckedStatusBooked"
      >
        Забронировано
      </base-checkbox>
      <base-checkbox
        class="status-list__checkbox"
        :withText="true"
        v-model="isCheckedStatusSold"
      >
        Продано
      </base-checkbox>
      <base-checkbox
        class="status-list__checkbox"
        :withText="true"
        v-model="isCheckedStatusActive"
      >
        Активно
      </base-checkbox>
    </div>
  </div>
</template>

<script>
import IconDropdown from "@/components/icons/IconDropdown.vue";

export default {
  name: "status-list",
  components: {
    IconDropdown,
  },
  data() {
    return {
      isVisible: false,
      isCheckedStatusBooked: false,
      isCheckedStatusSold: false,
      isCheckedStatusActive: false,
    };
  },
  methods: {
    showStatusList() {
      this.isVisible = !this.isVisible;
    },
  },
};
</script>

<style lang="scss" scoped>
.status-list {
  width: 190px;
  position: relative;

  &__toggle {
    padding: 9px 9px 9px 14px;
    border: 1px solid #c4c4c4;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
  }

  &__icon {
    transform: rotatez(0deg);
    transition: transform 0.3s ease-in;

    &._is-active {
      transform: rotatez(180deg);
    }
  }

  &__popover {
    position: absolute;
    z-index: 1;
    left: 0;
    top: 100%;
    width: 100%;
    padding: 18px 20px 21px;
    background: #ffffff;
    box-shadow: 0px 20px 25px -5px rgba(26, 32, 44, 0.1),
      0px 10px 10px -5px rgba(26, 32, 44, 0.04);
    transform: translateY(10px);
    margin-top: 6px;
    opacity: 0;
    visibility: hidden;
    transition: transform 0.2s ease-out, opacity 0.2s ease-out,
      visibility 0.2s ease-out;

    &._is-visible {
      opacity: 1;
      visibility: visible;
      transform: translateY(0px);
      transition: transform 0.2s ease-in, opacity 0.2s ease-in,
        visibility 0.2s ease-in;
    }
  }

  &__checkbox {
    padding-top: 17px;

    &:first-child {
      padding-top: 0;
    }
  }
}
</style>
