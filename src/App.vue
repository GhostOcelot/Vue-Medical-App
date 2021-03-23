<template>
	<Header />
	<Buttons :filter="filter" :activeButton="activeButton" />
	<PatientsList :patients="patients" :currentPatients="currentPatients" />
	<button @click="scrollToTop" class="top">
		<i class="fas fa-arrow-up"></i>
	</button>
</template>

<script>
import Header from "./components/Header.vue"
import Buttons from "./components/Buttons.vue"
import PatientsList from "./components/PatientsList.vue"

export default {
	name: "App",
	components: {
		Header,
		Buttons,
		PatientsList,
	},
	data() {
		return {
			patients: [],
			currentPatients: [],
			activeButton: "all",
		}
	},
	methods: {
		async fetchPatients() {
			const patientsWithMedications = []
			const patientsRes = await fetch("https://cerber.pixel.com.pl/api/patients")
			const patientsData = await patientsRes.json()
			const medicationRes = await fetch("https://cerber.pixel.com.pl/api/medicine")
			const medicationData = await medicationRes.json()
			patientsData.forEach(patient => {
				const patientMedications = []
				medicationData.forEach(medication => {
					if (medication.patientIds.includes(patient.id)) {
						patientMedications.push(medication)
					}
				})
				patientsWithMedications.push({
					patientData: patient,
					patientMedications: patientMedications,
				})
			})
			this.patients = patientsWithMedications
			this.currentPatients = patientsWithMedications
		},

		filter(e) {
			this.activeButton = e.target.name

			switch (e.target.name) {
				case "over-30":
					this.currentPatients = this.patients.filter(patient => patient.patientData.age > 30)
					break
				case "men":
					this.currentPatients = this.patients.filter(
						patient => patient.patientData.gender === "male"
					)
					break
				default:
					this.currentPatients = this.patients
			}
		},
		scrollToTop() {
			window.scrollTo({ top: 0, behavior: "smooth" })
		},
	},
	created() {
		this.fetchPatients()
	},
}
</script>

<style>
* {
	padding: 0;
	margin: 0;
	box-sizing: border-box;
}

body {
	background: #b8e3f1;
	font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu",
		"Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
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
	outline: none;
	cursor: pointer;
}

/* .top:hover {
	transform: scale(1.1);
} */

.fas {
	font-size: 20px;
}
</style>
