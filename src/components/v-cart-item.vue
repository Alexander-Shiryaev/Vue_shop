<template>
  <div class="v-cart-item">
    <img
      class="v-cart-item__image"
      :src="require('../assets/images/' + cart_item_data.image)"
      alt="image"
    />
    <div class="v-cart-item__info">
      <p>{{ cart_item_data.name }}</p>
      <p>{{ cart_item_data.price }}</p>
      <p>{{ cart_item_data.article }}</p>
    </div>
    <div class="v-cart-item__quantity">
      <p>Кол-во:</p>
      <span>
        <button class="quantity__btn" @click="decrementItem">-</button>
        {{ cart_item_data.quantity }}
        <button class="quantity__btn" @click="incrementItem">+</button>
      </span>
    </div>
    <button 
      class="btn" 
      @click="deleteFromCart"
      >
      Убрать из корзины
    </button>
  </div>
</template>

<script>
export default {
  name: "v-cart-item",
  props: {
    cart_item_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    decrementItem() {
      this.$emit("decrement");
    },

    incrementItem() {
      this.$emit("increment");
    },

    deleteFromCart() {
      this.$emit("deleteFromCart");
    },
  },
};
</script>

<style lang="scss">
.v-cart-item {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 0 8px 0 #e0e0e0;
  padding: $padding * 2;
  margin: 0 0 $margin * 2 0;
  &__image {
    max-width: 50px;
  }
}

.quantity__btn {
  cursor: pointer;
  background: #fff;
  border: 1px solid #555;
  border-radius: $radius;
  outline: none;
  &:hover {
    background: #ececec;
  }
  &:active {
    background: #fff;
  }
}
</style>