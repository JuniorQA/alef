<template>
	<div class="flex no-wrap credenctial-group">
		<mainInput v-for="(item, index) in placeholderCredentials" v-bind:key = 'item' v-bind:index = 'index' v-bind:item = 'item'/>
		<deleteBtn @removeItem ="removeItem"/>
	</div>
</template>

<script>
	import mainInput from '@/components/input'
	import deleteBtn from '@/components/deleteBtn'

	export default {
		name: 'credentialGroup',
		props : ['placeholderCredentials', 'childQuantity'], 
		data(){
			return{

			}
		},
		methods:{
		removeItem(e, childQuantity) {
			let divContainer = document.querySelectorAll('.credenctial-group');
			let deleteBtns = document.querySelectorAll('.delete-btn');
				for (var i = 0; i < deleteBtns.length; i++) {
					if (e === deleteBtns[i]) {
						console.log(childQuantity);
						childQuantity--;
						console.log(childQuantity);
						divContainer[i].remove();
					}
				}
		}
		},
		components: {
			mainInput,
			deleteBtn,
		}
	}
</script>