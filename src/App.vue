<template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
      	<div class="row">
      		<div class="col-md-6" :key="product.id" v-for="product in Products">
      			<Product :isInCart="isInCart(product)" v-on:add-to-cart="addToCart(product)" :product="product"></Product>

      		</div>
      	</div>
      </div>
      <div class="col-md-5 my-5">
      	<Cart v-on:pay="payNow()" v-on:remove-product="RemoveItem($event)" :items="cart"></Cart>
      </div>
    </div>
  </div>
</template>

<script>
import Products from '@/products.json'
import Product from '@/components/Product.vue'
import Cart from '@/components/Cart.vue'
export default {
  name: 'app',
  components:{
  	Product,
  	Cart
  },
  data(){
  	return{
  		Products,
  		cart:[]
  	}
  },
  methods:{
  	addToCart(Product){
  		this.cart.push(Product)
  	},
  	isInCart(Product){
  		const Item = this.cart.find(Item => Item.id === Product.id)
  		if(Item){
  			return true
  		}
  		return false
  	},
  	RemoveItem(product){
  		this.cart = this.cart.filter(item => item.id !== product.id)
  	},
  	payNow(){
  		this.cart = []
  		alert('Shopping Completed')
  	}
  }
  
}
</script>

