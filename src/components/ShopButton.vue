<template>
    <div>
		<button v-if="count <= 0" class="btn w-100 btn-success" @click="buy(1)">
			COMPRAR <span class="fa-solid fa-cart-plus"></span>
		</button>
		<div v-else class="d-flex justify-content-between align-items-center">
			<b-button class="btn w-25 btn-success" @click="buy(-1)">
				<span class="text-align-center"><b-icon icon="dash-lg" aria-hidden="true" animation="throb"></b-icon></span>
			</b-button>
			{{count}}
			<b-button class="btn w-25 btn-success" @click="buy(1)">
				<span class="text-align-center"><b-icon icon="plus-lg" aria-hidden="true" animation="throb"></b-icon></span>
			</b-button>
		</div>
    </div>
</template>

<script>
export default {
    props: {product: Object,carrito: Array},
        data(){return {
        }
    },
        computed:{
            count(){
                let item = this.carrito.find(i => i.product.id == this.product.id)
                return item ? item.count : 0
            },
        },
        methods: {
            buy(count) {
                this.$emit('buy',{product:this.product,sum:count})
            }
        },
}
</script>

<style>

</style>