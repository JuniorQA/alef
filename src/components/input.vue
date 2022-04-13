<template>
	<input type="text" class="main-input" v-bind:placeholder='item'>
</template>

<script>
	export default {
		name: 'mainInput',
		props : ['placeholderCredentials', 'item',], 
		data(){
			return{
				
			}
		},
		methods: {

		}

	}
</script>