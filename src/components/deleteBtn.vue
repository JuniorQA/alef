<template>
	<div><button class="delete-btn" v-on:click="$emit('removeItem', $event.target, childQuantity)">Удалить</button></div>
</template>

<script>
	export default {
		name: 'deleteBtn',
		props : ['childQuantity'], 
		data(){
			return{
				
			}
		}
	}
</script>