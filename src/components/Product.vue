<template>
	<div class="card my-5">
		<div class="card-body">
			<h5 class="card-title text-center">{{product.title}}</h5>
			<p class="text-center text-muted card-text display-4">
			${{Number(product.price).toFixed()}}</p>
			<button :disabled="isInCart" @click="$emit('add-to-cart',product)" class="btn btn-primary form-control">{{ isInCart ? 'Added To Cart': 'Add To Cart'}}</button>
		</div>
	</div>
</template>
<script>
	export default{
		props:['product','isInCart']
	}
</script>