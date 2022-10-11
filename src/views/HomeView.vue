<template>
  <div class="home">
    <h1>GARDEN SUSHI</h1>
	<b-button class="btn btn-success" @click="getProducts()"> Ver Productos</b-button>
    <div>
      <b-container class="bv-example-row">
          <b-row>
              <b-col v-for="product in products" :key="product.id">
                <ProductsCards :product="product" @buy="addItem($event)" :carrito="carrito"/>
              </b-col>
          </b-row>
      </b-container>
    </div>
	<span class="total ">
		TOTAL: $ {{ total }}
	</span>
  </div>
</template>

<script>
// @ is an alias to /src
import ProductsCards from '../components/ProductsCards.vue'

export default {
  name: 'HomeView',
  components: {
    ProductsCards,
  },
  data() {
		return {
			carrito: [],
			products: [
				
			],
			URL: "https://62e7262f0e5d74566aef7f19.mockapi.io/products"
		};
	},
  computed: {
		total() {
			let res = 0;
			this.carrito.forEach((item) => {
				res += item.product.price * item.count;
			});
			return res;
		},
	},
	methods: {
		addItem(item) {
			let itemExists = false
			this.carrito.forEach((listItem) => {
				if (listItem.product.id == item.product.id) {
					listItem.count += item.sum;
					itemExists = true
				}
			});
			if (!itemExists) {
				this.carrito.push({product:item.product,count:1});
			}
		},
		async getProducts(){
			const controller = new AbortController()
			setTimeout(() => {
				controller.abort()
			}, 2000);

			await fetch(this.URL, {
				signal: controller.signal
			})
			.then((response) => response.json())
			.then((json) => this.products = json)
			.catch((err) => {
				if (err.name == "AbortError") {
					console.log('error por limitacion de tiempo')
				} else {
					console.log('error', err.name)
				}
			})
			.finally(() => console.log('peticion terminada'))
		}
	},
};
</script>
<style scoped>
.total{
    height: 50px;
	width: 90px;
    position: fixed;
    right: 1%;
    bottom: 8%;
    box-shadow: 5px -5px 5px;
    background-color: #48887A;
}
</style>