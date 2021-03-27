<template>
	<div class="search-bar-container">
		<form class="search-bar-wrapper" @submit.prevent="search">
			<input type="text" id="search-bar" class="search-bar" placeholder="search..." />
			<button class="search-btn">
				<i class="fas fa-search fa-lg"></i>
			</button>
		</form>
	</div>
</template>

<script>
export default {
	name: "SearchBar",
	props: {
		searchPhrase: String,
	},
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
	margin: 40px 0 20px 0;
	display: flex;
	align-items: center;
}

.search-bar {
	padding: 15px;
	border: none;
	width: 95%;
}

.search-bar:focus,
.search-btn:focus {
	outline: thin dotted;
}

.search-btn {
	background: #fff;
	box-sizing: border-box;
	height: 100%;
	border: none;
	cursor: pointer;
	margin-left: 10px;
}

.fas {
	color: #ddd;
	margin: 0 15px;
}
</style>
