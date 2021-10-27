<template>
  <div class="cart">
    <header class="cart__header">
      <cart-header />
    </header>
    <main class="cart__body">
      <cart-body />
    </main>
  </div>
</template>

<script>
import CartBody from "@/components/CartBody.vue";
import CartHeader from "@/components/CartHeader.vue";

export default {
  name: "App",
  components: {
    CartBody,
    CartHeader,
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #f7f6f4;
  color: #000000;
}

#app {
  @import url("https://fonts.googleapis.com/css2?family=PT+Sans:wght@400;700&display=swap");
  font-family: "PT Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-weight: normal;
  font-size: 14px;
  line-height: 18px;
  min-height: 100vh;
}

.cart {
  max-width: 1050px;
  padding: 89px 24px 84px;
  margin: 0 auto;
}
</style>
