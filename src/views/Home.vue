<template>
  <section class="container">
    <range-selector :products="filteredProducts" v-model="max" />

    <product-list :products="filteredProducts" />
  </section>
</template>

<script>
// @ is an alias to /src
import ProductList from "../components/ProductList.vue";
import RangeSelector from "@/components/RangeSelector.vue";
export default {
  name: "Home",
  components: {
    ProductList,
    RangeSelector,
  },
  props: ["products"],
  data: function () {
    return {
      max: 50,
      cart: [],
    };
  },
  computed: {
    filteredProducts() {
      return this.products.filter((item) => item.price < Number(this.max));
    },
  },
};
</script>
