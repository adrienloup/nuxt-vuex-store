<template>
  <div id="article">
    <div v-if="cartTotal > 0" class="inside">
      <h1>Cart</h1>
      <div class="item" v-for="item in cart" v-bind:key="item.id">
        <img class="img" :src="`/${item.img}`" :alt="`Image of ${item.name}`">
        <div class="text">
          <strong>{{ item.name }}</strong>
          <no-ssr><span>{{ item.price | usdollar }} x {{ item.count }}</span></no-ssr>
          <no-ssr><span>Total for this item: <strong>{{ item.price * item.count }}</strong></span></no-ssr>
        </div>
      </div>
      <div class="total">
        <strong>Total: {{ total | usdollar }}</strong>
      </div>
    </div>
    <div v-else-if="cartTotal === 0 && success === false" class="inside">
      <h1>Cart</h1>
      <p>You are the best but your cart is empty. You can find all the clothes you are looking for without being disturbed :)</p>
      <nuxt-link exact to="/"><button>Go shopping</button></nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      success: false
    };
  },
  computed: {
    cart() {
      return this.$store.state.cart
    },
    cartTotal() {
      return this.$store.state.cartTotal
    },
    total() {
      return Object.values(this.cart)
        .reduce((acc, el) => acc + (el.count * el.price), 0)
        .toFixed(2);
    }
  },
  filters: {
    usdollar: function(value) {
      return `$${value}`
    }
  }
}
</script>
