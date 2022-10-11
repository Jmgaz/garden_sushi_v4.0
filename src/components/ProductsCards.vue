<template>
    <b-card 
    :img-src="product.img | url" 
    img-top
    >
      <div class="card-body text-center">
        <h5 class="card-title fw-bold">{{product.name}}</h5>
        <h5>$ {{product.price}}</h5>
        <ShopButton :product="product" @buy="$emit('buy',$event)" :carrito="carrito"/>            
      </div>
    </b-card>
  
  
</template>

<script>
import ShopButton from "./ShopButton";
export default {
components: { ShopButton },
	props: {
		product: Object,
		carrito: Array,
	},

}

</script>

<style scoped>
.card {
  font-family: roboto, sans-serif;
  letter-spacing: 1px;
  font-weight: 600;
  color: #575757;
  background-color: #F1F1F180;
}
</style>