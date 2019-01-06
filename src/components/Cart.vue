<template>
	<div>
		<ul class="list-group">
			<li class="list-group-item" v-for="item in items" :key="item.id">
				{{item.title}} - 
				$ {{item.price}}
				<button @click="$emit('remove-product',item)" class="btn btn-danger float-right badge">Remove From Cart</button>
			</li>
		</ul>
		<div class="card my-5 p-3">
			<h4 class="text-center">Total: $ {{ total }}</h4>
		</div>
		<button :disabled="items.length === 0" @click="$emit('pay')" class="btn btn-warning form-control">Pay Now</button>
	</div>
</template>
<script>
	export default{
		props:['items'],
		computed:{
			total(){
				return this.items.reduce((acc,item) => acc + Number(item.price),0)
			}
		}
	}
</script>