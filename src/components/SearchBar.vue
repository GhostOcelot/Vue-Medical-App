<template>
	<div class="search-bar-container">
		<div class="search-bar-wrapper">
			<!-- <label for="search-bar">Search for patient:</label> -->
			<input
				@input="e => search(e)"
				type="text"
				id="search-bar"
				class="search-bar"
				placeholder="search..."
			/>
			<i class="fas fa-search fa-lg"></i>
		</div>
	</div>
</template>

<script>
export default {
	name: "SearchBar",

	methods: {
		search(e) {
			this.$emit("search", e)
		},
	},
}
</script>

<style scoped>
.search-bar-container {
	display: flex;
	justify-content: center;
	margin: 0 15px;
}

.search-bar-wrapper {
	width: 500px;
	max-width: 100%;
	background: #fff;
	margin-bottom: 10px;
	display: flex;
	align-items: center;
}

.search-bar {
	padding: 15px;
	border: none;
	width: 95%;
}

.search-bar:focus {
	outline: thin dotted;
}

.fas {
	color: #ddd;
	margin: 0 15px;
}
</style>
