<template>
  <div>
    <HomeCarousel :sale_items="sale_items" />
    <v-container>
      <h1 class="text-md-h4 text-h6 mt-5">Check these out 🔥</h1>
      <ProductSlider class="mt-5" :products="products" />
      <Newsletter class="mt-5" />
    </v-container>
  </div>
</template>

<script>
export default {
  async created() {
    this.sale_items = await this.$content("products").where({ onSale: true }).fetch();
    this.products = await this.$content("products").fetch();
  },
  data: () => ({
    products: null,
    sale_items: null,
  }),
};
</script>

<style></style>
