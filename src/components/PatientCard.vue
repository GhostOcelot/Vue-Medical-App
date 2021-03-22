<template>
	<li class="patients-list-item">
		<div class="patient-basic-data">
			<h2 class="patient-name">
				{{ index + 1 }}. {{ patient.patientData.name }} {{ patient.patientData.lastName }}
			</h2>
			<h4 class="patient-age">{{ patient.patientData.age }} years old</h4>
		</div>

		<h4 class="medication-header">Medications applied:</h4>
		<ul
			:key="medication.id"
			class="medication-list"
			v-for="medication in patient.patientMedications"
		>
			<li class="medication-list-item" key="{medication.id}">
				{{ medication.medicationName }}
			</li>
		</ul>
	</li>
</template>

<script>
export default {
	name: "PatientsCard",
	props: {
		patient: Object,
		index: Number,
	},
}
</script>

<style scoped>
.patients-list-item {
	background: #fff;
	width: 500px;
	max-width: 100%;
	list-style: none;
	padding: 20px;
	margin: 20px 0;
	border-top: 10px solid #a809ae;
}

.medication-list {
	margin-top: 3px;
}

.medication-list-item {
	list-style: none;
}

.patient-basic-data {
	margin-bottom: 5px;
}

.patient-name {
	color: #a809ae;
	margin-bottom: 5px;
}

.patient-age {
	padding-bottom: 15px;
	border-bottom: 1px solid #b8e3f1;
}

.medication-header {
	margin: 15px 0 10px 0;
}
</style>
