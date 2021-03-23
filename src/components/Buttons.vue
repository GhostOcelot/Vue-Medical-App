<template>
	<div class="filter-btn-container">
		<button
			@click="filter"
			:class="[activeButton === 'all' ? 'active' : null, 'filter-btn']"
			name="all"
		>
			All Patients
		</button>

		<button
			@click="filter"
			:class="[activeButton === 'over-30' ? 'active' : null, 'filter-btn']"
			name="over-30"
		>
			30 years old +
		</button>

		<button
			@click="filter"
			:class="[activeButton === 'men' ? 'active' : null, 'filter-btn']"
			name="men"
		>
			Men only
		</button>
	</div>
</template>

<script>
export default {
	name: "Buttons",
	props: {
		activeButton: String,
	},
	methods: {
		filter(e) {
			this.$emit("filter", e)
		},
	},
}
</script>

<style scoped>
.filter-btn-container {
	display: flex;
	justify-content: center;
	margin: 0 10px 30px 10px;
}

.filter-btn {
	background: #fff;
	position: relative;
	margin: 0 5px;
	width: 160px;
	height: 50px;
	border: none;
	border-bottom: 10px solid #fcd1fd;
	outline: none;
	cursor: pointer;
}

.filter-btn.active {
	border-bottom: 10px solid #a809ae;
}

.filter-btn:before {
	content: "";
	display: block;
	position: absolute;
	top: 30px;
	height: 10px;
	width: 100%;
	border-bottom: 10px solid #a809ae;
	transform: scaleX(0);
	transition: 0.2s;
}

.filter-btn:hover:before {
	transform: scaleX(1);
}
</style>
