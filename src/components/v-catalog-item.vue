<template>
  <div class="v-catalog-item">
    <img
      class="v-catalog-item__image"
      :src="require('../assets/images/' + product_data.image)"
      alt="image"
    />
    <p class="v-catalog-item__name">{{ product_data.name }}</p>
    <p class="v-catalog-item__model">{{ product_data.model }}</p>
    <p class="v-catalog-item__color">{{ product_data.color }}</p>
    <p class="v-catalog-item__price">Цена: {{ product_data.price }} &#8381;</p>
    <button
      class="v-catalog-item__add_to_cart_btn btn"
      @click="addToCart"
    >
      В корзину
    </button>
  </div>
</template>

<script>
export default {
  name: "v-catalog-item",
  props: {
    product_data: {
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
    addToCart() {
      this.$emit('addToCart', this.product_data)
    }
  },
    mounted() {
    this.$set(this.product_data, "quantity", 1);
  },
};
</script>

<style lang="scss">
.v-catalog-item {
  flex-basis: 20%;
  box-shadow: 0 0 8px 0 #e0e0e0;
  padding: $padding * 2;
  margin: 0 0 $margin * 2 0;
  &__image {
    height: 100px;
  }
  &:hover {
    box-shadow: 0 0 8px 8px #eee;
  }
}
</style>