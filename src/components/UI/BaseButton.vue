<template>
  <button class="base-button">
    <div class="base-button__inner">
      <span>{{ buttonText }}</span>
      <div class="base-button__icon">
        <slot></slot>
      </div>
    </div>
  </button>
</template>

<script>
export default {
  name: "base-button",
  props: {
    buttonText: String,
  },
};
</script>

<style lang="scss" scoped>
.base-button {
  padding: 7px 13px;
  border: none;
  background: #e5e5e5;
  font-size: 13px;
  line-height: 20px;
  transition: background 0.2s ease-out;
  cursor: pointer;

  &:hover {
    background: #c7c7c7;
  }

  &__inner {
    display: flex;
    justify-content: center;
    align-items: center;

    span {
      padding-right: 6px;
    }
  }

  &__icon {
    display: inline-flex;
  }
}
</style>
