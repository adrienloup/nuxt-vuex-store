<template>
  <div id="filter">
    <label for="pricerange">Price: <span>${{ pricerange }}</span></label>
    <input class="slider" id="pricerange" type="range" :value="pricerange"  :min="min" :max="max" step="0.1" @input="$emit('update:pricerange', $event.target.value)"/>
    <ul>
      <li>Genre</li>
      <li>Brand</li>
      <li>Collection</li>
      <li>Color</li>
      <li>Size</li>
      <li>Product type</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    sale: {
      type: Boolean,
      default: false
    },
    pricerange: {
      type: [Number, String],
      default: 500
    }
  },
  data() {
    return {
      min: 0,
      max: 500
    }
  }
}
</script>

<style lang="scss" scoped>
#filter {
  width: calc((100%/4) - 50px);
  height: 40px;
  margin: 0 10px 10px 0;
  padding: 20px;

  ul {
    list-style-type: none;
  }
  
  li{
    padding: 10px 0;
    border-bottom: 1px solid #eee;

    &:last-child {
      border: none;
    }
  }
}
@media screen and (max-width: 1200px) {

	#filter {
		width: calc((100% / 3) - 50px);
	}
}
@media screen and (max-width: 769px) {

	#filter {
		width: calc((100% / 2) - 50px);
	}
}
input[type='range'].slider {
  -webkit-appearance: none;
  width: 100%;
}
input[type='range'].slider:focus {
  outline: none;
}
input[type='range'].slider::-webkit-slider-runnable-track {
  width: 100%;
  height: 5px;
  cursor: pointer;
  box-shadow: 0px 0px 0px rgba(0, 0, 0, 0), 0px 0px 0px rgba(13, 13, 13, 0);
  background: #d01345;
  border: 0px solid rgba(1, 1, 1, 0);
}
input[type='range'].slider::-webkit-slider-thumb {
  box-shadow: 0px 0px 0px rgba(0, 0, 62, 0), 0px 0px 0px rgba(0, 0, 88, 0);
  border: 1.9px solid #d01345;
  height: 18px;
  width: 18px;
  border-radius: 31px;
  background: #d01345;
  cursor: pointer;
  -webkit-appearance: none;
  position: relative;
  top: -7px;
  right: -2px;
}
input[type='range'].slider::-moz-range-track {
  width: 100%;
  height: 5px;
  cursor: pointer;
  box-shadow: 0px 0px 0px rgba(0, 0, 0, 0), 0px 0px 0px rgba(13, 13, 13, 0);
  background: #d01345;
  border: 0px solid rgba(1, 1, 1, 0);
}
input[type='range'].slider::-moz-range-thumb {
  box-shadow: 0px 0px 0px rgba(0, 0, 62, 0), 0px 0px 0px rgba(0, 0, 88, 0);
  border: 1.9px solid #d01345;
  height: 17px;
  width: 17px;
  border-radius: 31px;
  background: #ffffff;
  cursor: pointer;
}
input[type='range'].slider::-ms-track {
  width: 100%;
  height: 5px;
  cursor: pointer;
  background: transparent;
  border-color: transparent;
  color: transparent;
}
</style>
