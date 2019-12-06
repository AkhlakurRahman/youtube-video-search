<template>
	<div>
		<input type="search" @input="onInput" />
	</div>
</template>

<script>
export default {
	name: 'SearchBar',
	methods: {
		onInput: function(event) {
			this.$emit('searchInput', event.target.value);
		}
	}
};
</script>

<style scoped></style>
