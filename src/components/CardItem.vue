<template>
  <div class="card-item">
    <div class="card-item__checkbox">
      <base-checkbox v-model="isChecked" />
    </div>
    <div class="card-item__body">
      <div class="card-item__status">{{ statusName }}</div>

      <div class="card-item__info">
        <div class="card-item__head">
          <div class="card-item__price">{{ price }} руб.</div>
          <div class="card-item__type">
            <div v-if="isFlat" class="card-item__type-icon">
              <icon-flat />
            </div>
            <div v-else class="card-item__type-icon">
              <icon-car />
            </div>
            <span>{{ cardType }}</span>
            <div class="card-item__type-desc">{{ cardTypeDesc }}</div>
          </div>
          <div class="card-item__name">
            {{ name }}, <span>{{ building }}</span>
          </div>
        </div>
        <div class="card-item__specs">
          <div class="card-item__specs-col">
            <div class="card-item__spec">{{ number }}</div>
            <div v-if="isFlat" class="card-item__spec">
              {{ rooms }} комн. кв.
            </div>
          </div>
          <div class="card-item__specs-col">
            <div class="card-item__spec">{{ square }} м²</div>
            <div v-if="isFlat" class="card-item__spec">{{ floor }} этаж</div>
          </div>
        </div>
        <div class="card-item__location">
          <div class="card-item__location-text">
            <div class="card-item__location-pin"><icon-pin /></div>
            <span>
              {{ location }}
            </span>
          </div>
        </div>
      </div>
      <div class="card-item__picture">
        <div class="card-item__img">
          <img alt="flat image" src="../assets/flat.png" />
        </div>
        <div class="card-item__date">{{ date }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import IconFlat from "@/components/icons/IconFlat.vue";
import IconCar from "@/components/icons/IconCar.vue";
import IconPin from "@/components/icons/IconPin.vue";

export default {
  name: "CardItem",
  components: {
    IconFlat,
    IconCar,
    IconPin,
  },
  props: {
    statusName: String,
    price: String,
    cardType: String,
    cardTypeDesc: String,
    number: String,
    rooms: String,
    square: String,
    floor: String,
    name: String,
    building: String,
    location: String,
    date: String,
    isFlat: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      isChecked: false,
    };
  },
};
</script>

<style lang="scss" scoped>
.card-item {
  $that: &;

  padding: 21px 24px 24px;
  border: 1px solid #e5e5e5;
  background: #ffffff;
  min-height: 238px;

  display: flex;
  position: relative;

  &__status {
    position: absolute;
    right: 0;
    top: 21px;
    padding: 6px 9px 6px 23px;

    &::before {
      content: "";
      position: absolute;
      left: 9px;
      top: 12px;
      width: 6px;
      height: 6px;
      border-radius: 100%;
    }

    ._is-entity & {
      color: #dd4c5d;
      background: #ffe4e4;

      &::before {
        background: #dd4c5d;
      }
    }
    ._is-private & {
      color: #0291c1;
      background: #d6f5ff;

      &::before {
        background: #0291c1;
      }
    }
    ._is-booked & {
      color: #686868;
      background: #ededed;

      &::before {
        background: #686868;
      }
    }
    ._is-sold & {
      color: #808080;
      background: #cccccc;

      &::before {
        background: #808080;
      }
    }
  }

  &__checkbox {
    display: flex;
    align-items: center;
  }
  &__body {
    display: flex;
    justify-content: space-between;
    padding-left: 25px;
  }
  &__info {
    display: flex;
    flex-direction: column;
  }
  &__head {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: center;
  }
  &__price {
    font-weight: bold;
    font-size: 15px;
    line-height: 20px;
    color: #ff0d29;
    padding-right: 16px;
  }
  &__type {
    font-size: 12px;
    line-height: 16px;
    color: #232735;
    box-shadow: 0px 0px 2px rgba(94, 119, 157, 0.25);
    border-radius: 32px;
    padding: 5px 16px;
    cursor: pointer;
    position: relative;

    display: flex;
    justify-content: center;
    align-items: center;

    &:hover {
      #{$that}__type-desc {
        opacity: 1;
      }
    }

    span {
      padding-left: 8px;
    }
  }
  &__type-icon {
    flex: none;
    display: inline-flex;
  }
  &__type-desc {
    position: absolute;
    left: calc(50% - 16px);
    top: 100%;
    margin-top: 12px;
    background: rgba(26, 32, 44, 0.65);
    padding: 12px 18px;
    font-weight: normal;
    font-size: 13px;
    line-height: 155%;
    font-feature-settings: "zero" on;
    color: #ffffff;
    white-space: nowrap;

    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s ease-out;

    &::before {
      content: "";
      position: absolute;
      left: 8px;
      bottom: 100%;
      border: 8px solid transparent;
      border-bottom: 7px solid rgba(26, 32, 44, 0.65);
    }
  }
  &__name {
    line-height: 150%;
    flex-grow: 1;
    padding-top: 3px;
    min-height: 45px;
    max-width: 240px;

    span {
      color: #808080;
    }
  }
  &__specs {
    line-height: 25px;
    display: flex;
    padding-top: 14px;
  }
  &__specs-col {
    &:nth-child(even) {
      border-left: 1px solid #c4c4c4;
      padding-left: 20px;
    }
    &:nth-child(odd) {
      padding-right: 20px;
    }
  }
  &__location {
    line-height: 150%;
    padding-top: 16px;
    min-height: 58px;
    display: flex;
    justify-content: flex-start;
    align-items: flex-end;
    flex-grow: 1;
    max-width: 214px;
  }
  &__location-text {
    display: flex;
    position: relative;
  }
  &__location-pin {
    position: absolute;
    right: calc(100% + 6px);
    top: 4px;
    display: flex;
  }
  &__picture {
    padding-top: 57px;
  }
  &__img {
    display: flex;
  }
  &__date {
    font-size: 13px;
    line-height: 20px;
    text-align: right;
    color: #9b9b9b;
    padding-top: 17px;
    white-space: nowrap;
  }
}
</style>
