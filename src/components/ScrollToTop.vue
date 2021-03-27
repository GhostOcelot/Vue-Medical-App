<template>
	<button @click="scrollToTop" class="top">
		<i class="fas fa-arrow-up"></i>
	</button>
</template>

<script>
export default {
	name: "ScrollToTop",
	methods: {
		scrollToTop() {
			this.$emit("scroll-to-top")
		},
	},
}
</script>

<style scoped>
.top {
	position: fixed;
	bottom: 15px;
	right: 15px;
	width: 40px;
	height: 40px;
	border: none;
	background: #a809ae;
	color: #fff;
	transition: 0.3s;
	cursor: pointer;
}

.top:focus {
	outline: thin dotted;
}

.fas {
	font-size: 20px;
}
</style>
