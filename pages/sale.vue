<template>
  <article id="article">
    <app-filter :pricerange.sync="highprice"/>
    <app-item v-for="(item, index) in saleProducts" v-bind:key="item.id" :item="item" :index="index"/>
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
    saleProducts() {
      return this.$store.getters.sale.filter(el => el.price < this.highprice)
    }
  }
}
</script>
