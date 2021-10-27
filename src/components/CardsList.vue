<template>
  <ul class="cards-list">
    <li class="cards-list__item" v-for="card in cardsList" :key="card.id">
      <card-item
        :isFlat="card.isFlat"
        :statusName="card.statusName"
        :price="card.price"
        :cardType="card.cardType"
        :cardTypeDesc="card.cardTypeDesc"
        :number="card.number"
        :rooms="card.rooms"
        :square="card.square"
        :floor="card.floor"
        :name="card.name"
        :building="card.building"
        :location="card.location"
        :date="card.date"
        :class="{
          '_is-entity': card.status === 'entityAssignment',
          '_is-private': card.status === 'privateAssignment',
          '_is-booked': card.status === 'booked',
          '_is-sold': card.status === 'sold',
        }"
      />
    </li>
  </ul>
</template>

<script>
import CardItem from "@/components/CardItem.vue";

export default {
  name: "cards-list",
  components: {
    CardItem,
  },
  data() {
    return {
      cardsList: [
        {
          id: 1,
          status: "entityAssignment",
          statusName: "Уступка от юр. лица",
          price: "7 733 300",
          cardType: "Квартира",
          cardTypeDesc: "Квартира",
          number: "кв. 62",
          rooms: "1",
          square: "234.38",
          floor: "7",
          name: "Чистое Небо",
          building: "корпус 10, III кв. 2022 г.",
          location:
            "Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1",
          date: "Добавлено 21/11/2020",
        },
        {
          id: 2,
          status: "privateAssignment",
          statusName: "Уступка от физ. лица",
          price: "7 733 300",
          cardType: "Квартира",
          cardTypeDesc: "Квартира",
          number: "кв. 62",
          rooms: "1",
          square: "234.38",
          floor: "7",
          name: "Зеленый квартал на Пулковских высотах",
          building: "корпус 10, III кв. 2022 г.",
          location: "Комендантский пр., уч. 1 Каменка",
          date: "Добавлено 21/11/2020",
        },
        {
          id: 3,
          isFlat: false,
          status: "booked",
          statusName: "Забронировано",
          price: "800 300",
          cardType: "Паркинг",
          cardTypeDesc: "Подземная встроенно-пристроенная",
          number: "№ 7-10-2 (ПИБ №68)",
          square: "15",
          name: "Зеленый квартал на Пулковских высотах",
          building: "корпус 10, III кв. 2022 г.",
          location:
            "Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1",
          date: "Добавлено 21/11/2020",
        },
        {
          id: 4,
          isFlat: false,
          status: "sold",
          statusName: "Продано",
          price: "800 300",
          cardType: "Паркинг",
          cardTypeDesc: "Подземная встроенно-пристроенная",
          number: "№ 7-10-2 (ПИБ №68)",
          square: "15",
          name: "Зеленый квартал на Пулковских высотах",
          building: "корпус 10, III кв. 2022 г.",
          location:
            "Лен. область, Всеволожский район, д. Кудрово, ул. Столичная, д. 5, к. 1",
          date: "Добавлено 21/11/2020",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.cards-list {
  list-style: none;
  list-style-type: none;
  margin: 0;
  display: flex;
  flex-wrap: wrap;
  margin: -24px 0 0 -24px;

  &__item {
    flex: 1 1 50%;
    padding: 24px 0 0 24px;
  }
}
</style>
