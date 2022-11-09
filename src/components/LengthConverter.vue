<template>
	<div class="converter__body">
		<div class="converter">
			<h1 class="converter__title">Length Converter</h1>

			<div class="converter__inputField">
				<div class="converter__input">
					<input v-on:keyup="handleMyResult()" v-model="input" type="number" placeholder="Input" id="input" autocomplete="off">
					<select v-on:change="handleMyResult()" v-model="inputType" id="inputType">
						<option value="Millimeter">Millimeter</option>
						<option value="Centimeter">Centimeter</option>
						<option value="Meter">Meter</option>
						<option value="Kilometer">Kilometer</option>
					</select>
				</div>

				<span>=</span>

				<div class="converter__input">
					<input v-on:keyup="handleMyResult()" v-model="result" type="number" placeholder="Result" id="result" autocomplete="off">
					<select v-on:change="handleMyResult()" v-model="resultType" id="resultType">
						<option value="Millimeter">Millimeter</option>
						<option value="Centimeter">Centimeter</option>
						<option value="Meter">Meter</option>
						<option value="Kilometer">Kilometer</option>
					</select>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			input: '',
			result: '',
			resultType: 'Kilometer',
			inputType: 'Meter'
		}
	},

	// created() {
	// 	window.addEventListener('keyup', this.handleMyResult);
	// 	resultType.addEventListener('change', this.handleMyResult);
	// 	inputType.addEventListener('change', this.handleMyResult);
	// },

	// methods: {
	// 	handleMyResult() {
	// 		if (inputTypeValue === 'Millimeter' && resultTypeValue === 'Centimeter') {
	// 			this.result = this.input / 10; 
	// 		} else if (inputTypeValue === 'Millimeter' && resultTypeValue === 'Meter') {
	// 			this.result = this.input * 0.001;
	// 		} else if (inputTypeValue === 'Millimeter' && resultTypeValue === 'Kilometer') {
	// 			this.result = this.input / 1000000;
	// 		} else if (inputTypeValue === 'Millimeter' && resultTypeValue === 'Millimeter') {
	// 			this.result = this.input;
	// 		}

	// 		// if (inputTypeValue === 'centimeter' && resultTypeValue === 'millimeter') {
	// 		// 	result.value = Number(input.value) / 10; 
	// 		// } else if (inputTypeValue === 'centimeter' && resultTypeValue === 'meter') {
	// 		// 	result.value = Number(input.value) * 0.01;
	// 		// } else if (inputTypeValue === 'centimeter' && resultTypeValue === 'kilometer') {
	// 		// 	result.value = Number(input.value) * 0.00001;
	// 		// } else if (inputTypeValue === 'centimeter' && resultTypeValue === 'centimeter') {
	// 		// 	result.value = input.value;
	// 		// }

	// 		// if (inputTypeValue === 'meter' && resultTypeValue === 'millimeter') {
	// 		// 	result.value = Number(input.value) * 1000; 
	// 		// } else if (inputTypeValue === 'meter' && resultTypeValue === 'centimeter') {
	// 		// 	result.value = Number(input.value) * 100;
	// 		// } else if (inputTypeValue === 'meter' && resultTypeValue === 'kilometer') {
	// 		// 	result.value = Number(input.value) / 1000;
	// 		// } else if (inputTypeValue === 'meter' && resultTypeValue === 'meter') {
	// 		// 	result.value = input.value;
	// 		// }

	// 		// if (inputTypeValue === 'kilometer' && resultTypeValue === 'millimeter') {
	// 		// 	result.value = Number(input.value) * 1000000; 
	// 		// } else if (inputTypeValue === 'kilometer' && resultTypeValue === 'centimeter') {
	// 		// 	result.value = Number(input.value) * 100000;
	// 		// } else if (inputTypeValue === 'kilometer' && resultTypeValue === 'meter') {
	// 		// 	result.value = Number(input.value) / 1000;
	// 		// } else if (inputTypeValue === 'kilometer' && resultTypeValue === 'kilometer') {
	// 		// 	result.value = input.value;
	// 		// }
	// 	}
	// }	
}
</script>

<style scoped>

input, select {
	border-radius: 10px;
	border: none;
	padding: .5rem;
	background-color: #ffffff0f;
	margin-top: 1rem;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

select {
	cursor: pointer;
}

option {
	color: black;
}

span {
	margin-top: 1.5rem;
}

.converter__body {
	width: 100%;
	height: 100vh;
	display: flex;
	align-items: center;
	justify-content: center;
	background: linear-gradient(0deg, rgba(0, 0, 0, 0.8), 
	rgba(0, 0, 0, 0.8)), url(../assets/wallpaper.jpg);
}

.converter {
	background-color: #ffffff0f;
	border-radius: 10px;
	padding: 1rem;
}

.converter__title {
	font-size: 2.5rem;
	text-align: center;
}

.converter__inputField {
	display: flex;
	gap: 2rem;
}

.converter__input {
	display: flex;
	flex-direction: column;
}


@media screen and (max-width: 768px) {
	.converter__title {
		font-size: 2rem;
	}

	.converter__inputField {
		flex-direction: column;
		align-items: center;
		gap: 1rem;
	}
}
</style>