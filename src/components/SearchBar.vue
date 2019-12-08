<template>
	<div>
		<input type="search" placeholder="Search" @input="onInput" />
	</div>
</template>

<script>
export default {
	name: 'SearchBar',
	methods: {
		onInput(event) {
			this.$emit('searchInput', event.target.value);
		}
	}
};
</script>

<style scoped>
input {
	width: 60rem;
	padding: 0.7rem 0.5rem;
	border: 1px solid #8d8888;
}

input:focus,
input:active {
	border: 1px solid #000;
	outline: 1px solid #000;
}
</style>
