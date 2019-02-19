<template>
  <header id="header">
		<nuxt-link id="store" exact to="/">
			<app-svgstore/>
		</nuxt-link>
    <nav id="menu">
      <nuxt-link to="/sale"><span>Sale</span></nuxt-link>
      <nuxt-link to="/women">Women's</nuxt-link>
      <nuxt-link to="/men">Men's</nuxt-link>
    </nav>
    <nuxt-link to="/cart" id="cart" :class="{active: cartTotal > 0}">
			<span v-if="cartTotal > 0">{{ cartTotal }}</span>
			<app-svgcart/>
    </nuxt-link>
  </header>
</template>

<script>
import AppSvgstore from './AppSvgstore.vue'
import AppSvgcart from './AppSvgcart.vue'
export default {
  components: {
    AppSvgstore,
    AppSvgcart
  },
  computed: {
    cartTotal() {
      return this.$store.state.cartTotal
    }
  }
}
</script>

<style lang="scss" scoped>
#header {
	width: 100%;
	height: 80px;
	align-self: stretch;
	display: flex;
	flex-direction: row;
	align-items: stretch;
	justify-content: stretch;
	position: relative;
	z-index: 2;
}
#store {
	padding: 0 50px 0 40px;
	
	svg {
		width: 120px;
		margin-top: 2px;
	}

	path {
		fill: #2d2d2d;
	}
}
#menu {
	height: 100%;
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: stretch;
	list-style-type: none;

	a {
		display: block;
		height: 100%;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		padding: 0 40px;
		height: 100%;
		text-transform: uppercase;
		font-family: 'FTN75__W';
		color: #2d2d2d;

		&.nuxt-link-exact-active {
			background-color: #2d2d2d;
			color: #fff;
		}

		&:nth-child(1) {
			background: none;
			color: #fff;
			position: relative;

			span {
				position: relative;
				z-index: 2;
			}

			&::after {
					content: "";
					width: calc(100% + 20px);
					height: 100%;
					position: absolute;
					top: 0;
					left: -10px;
					z-index: 1;
					background-color: #d01345;
					transform: skew(-12deg);
			}
		}

		&:nth-child(2) {
			padding-left: 50px;
		}

		&:nth-child(1).nuxt-link-exact-active {
			background: none;
		}
	}
}
</style>
