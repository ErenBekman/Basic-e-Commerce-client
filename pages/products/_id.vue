<template>
  <div>
    <v-container v-if="product">
      <v-row justify="center">
        <v-col cols="11" md="7">
          <h2 class="text-center text-md-h4 font-weight-bold">
            {{ product.name }}
          </h2>
          <div class="mt-2 text-center">
            <v-rating readonly half-increments class="mb-2" color="yellow darken-2" background-color="grey lighten-1" :value="product.ratings" dense size="20"></v-rating>

            <v-chip class="ma-2" color="green" label text-color="white" v-for="(t, i) in product.tags" :key="`prod${product.id}-${i}`">
              <v-icon left> mdi-label </v-icon>
              {{ t }}
            </v-chip>
          </div>

          <v-img width="100%" class="el rounded-lg" height="50vh" :src="product.image"></v-img>
          <p class="mt-5 mb-7">
            {{ product.description }}
          </p>
          <v-btn @click="$store.commit('cart/AddToCart', product)" min-height="45" min-width="170" class="text-capitalize" color="green">Add To Cart</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  async created() {
    let d = await this.$content("products")
      .where({ id: parseInt(this.$route.params.id) })
      .limit(1)
      .fetch();
    this.product = d[0];
  },
  data: () => ({
    product: null,
  }),
};
</script>

<style></style>
