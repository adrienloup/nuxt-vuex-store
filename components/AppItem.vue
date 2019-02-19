<template>
  <div class="product" :class="{sale: item.sale}">
    <div class="img">
      <img :src="`/${item.img}`" :alt="`Image of ${item.name}`">
      <div @click="addItem">
        <app-svgcart/>
      </div>
    </div>
    <div class="caption">
      <span class="title">{{ item.name }}</span>
      <span class="sale" v-if="item.sale">Sale</span>
      <span class="price">{{ item.price | usdollar }}</span>
    </div>
  </div>
</template>

<script>
import AppSvgcart from './AppSvgcart.vue'
export default {
  components: {
    AppSvgcart
  },
  props: {
    item: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  filters: {
    usdollar: function(value) {
      return `$${value}`
    }
  },
  methods: {
    addItem() {
      this.$store.commit('addItem', this.item)
    }
  }
}
</script>
