<template>
  <article id="article">
    <app-filter :pricerange.sync="highprice"/>
    <app-item v-for="(item, index) in products" v-bind:key="item.id" :item="item" :index="index"/>
  </article>
</template>

<script>
import AppFilter from './../components/AppFilter.vue'
import AppItem from './../components/AppItem.vue'
export default {
  components: {
    AppFilter,
    AppItem
  },
  data() {
    return {
      highprice: 500
    }
  },
  computed: {
    products() {
      return this.$store.state.products.filter(el =>
        this.$store.state.sale
          ? el.price < this.highprice && el.sale
          : el.price < this.highprice
      );
    }
  }
}
</script>
