<template>
  <label class="base-checkbox">
    <input
      class="base-checkbox__input"
      type="checkbox"
      :checked="modelValue"
      @change="updateCheckbox"
    />
    <div class="base-checkbox__box">
      <div class="base-checkbox__checkmark">
        <icon-check />
      </div>
    </div>
    <div v-if="withText" class="base-checkbox__text">
      <slot></slot>
    </div>
  </label>
</template>

<script>
import IconCheck from "@/components/icons/IconCheck.vue";

export default {
  name: "base-checkbox",
  components: {
    IconCheck,
  },
  props: {
    modelValue: Boolean,
    withText: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    updateCheckbox(e) {
      this.$emit("update:modelValue", e.target.checked);
    },
  },
};
</script>

<style lang="scss" scoped>
.base-checkbox {
  $that: &;

  position: relative;
  display: inline-flex;
  justify-content: flex-start;
  align-items: center;
  min-height: 16px;
  padding-left: 18px;
  user-select: none;
  cursor: pointer;

  &:hover {
    #{$that}__text {
      color: #ff0d29;
    }
  }

  &__input {
    position: absolute;
    clip: rect(0 0 0 0);
    width: 1px;
    height: 1px;
    margin: -1px;
  }

  &__box {
    position: absolute;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 16px;
    height: 16px;
    border: 1px solid #c4c4c4;
    background: transparent;
    transition: border-color 0.25s ease-out, background-color 0.25s ease-out;

    #{$that}__input:checked ~ & {
      background-color: #fce66f;
    }
  }

  &__checkmark {
    opacity: 0;
    transition: opacity 0.25s ease-out;

    #{$that}__input:checked ~ #{$that}__box & {
      opacity: 1;
    }
  }

  &__text {
    color: #02101c;
    padding-left: 10px;
    transition: color 0.2s ease-out;
  }
}
</style>
