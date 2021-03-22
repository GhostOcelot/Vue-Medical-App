<template>
	<ul :key="patient.id" class="patients-list" v-for="(patient, index) in currentPatients">
		<PatientCard :patient="patient" :index="index" />
	</ul>
</template>

<script>
import PatientCard from "./PatientCard.vue"

export default {
	name: "PatientsList",
	props: {
		patients: Array,
		currentPatients: Array,
	},
	components: {
		PatientCard,
	},
}
</script>

<style scoped>
.patients-list {
	display: flex;
	flex-direction: column;
	flex-wrap: wrap;
	align-items: center;
	margin: 0 15px;
}
</style>
