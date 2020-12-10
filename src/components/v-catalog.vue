<template>
  <div class="v-catalog">
    <router-link :to="{ name: 'cart', params: { cart_data: CART } }">
      <span class="v-catalog__link_to_cart">Корзина: {{ CART.length }}</span>
    </router-link>
    <h1>Каталог</h1>
    <div class="v-catalog__list">
      <v-catalog-item
        v-for="product in PRODUCTS"
        :key="product.article"
        :product_data="product"
        @addToCart="addToCart"
      />
    </div>
  </div>
</template>

<script>
import vCatalogItem from "./v-catalog-item.vue";

import { mapActions, mapGetters } from "vuex";

export default {
  name: "v-catalog",
  components: {
    vCatalogItem,
  },
  props: {},
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["PRODUCTS", "CART"]),
  },
  methods: {
    ...mapActions(["GET_PRODUCTS_FROM_API", "ADD_TO_CART"]),
    addToCart(data) {
      this.ADD_TO_CART(data);
    },
  },
  mounted() {
    this.GET_PRODUCTS_FROM_API().then((response) => {
      if (response.data) {
        console.log("Data arrived!");
      }
    });
  },
};
</script>

<style lang="scss">
.v-catalog {
  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
  }
  &__link_to_cart {
    display: block;
    background: rgb(79, 55, 242);
    background: linear-gradient(
      90deg,
      rgba(79, 55, 242, 1) 0%,
      rgba(67, 80, 208, 1) 100%,
      rgba(77, 17, 207, 1) 100%
    );
    color: #fff;
    font-size: 16px;
    position: absolute;
    top: 10px;
    right: 10px;
    padding: $padding * 2;
    border-radius: 50px;
    &:hover {
      background: #fff;
      color: rgb(79, 55, 242);
      border: 1px solid rgb(79, 55, 242);
      box-sizing: border-box;
    }
    &:active {
      background: rgb(79, 55, 242);
      background: linear-gradient(
        90deg,
        rgba(79, 55, 242, 1) 0%,
        rgba(67, 80, 208, 1) 100%,
        rgba(77, 17, 207, 1) 100%
      );
      color: #fff;
    }
  }
}
</style>