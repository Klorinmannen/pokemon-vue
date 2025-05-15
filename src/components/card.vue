<script setup>
import { defineProps } from 'vue'
const props = defineProps({
	data: {
		type: Object,
		required: true
	}
})
</script>

<template>
	<div class="card">
		<div class="card-header">
			<div class="card-image">
				<img :src="`https://img.pokemondb.net/artwork/${data.name.toLowerCase()}.jpg`" alt="Pokemon Image"
					height="100" />
			</div>
			<div class="card-info">
				<div>Pokemon № {{ data.number }}</div>
				<div>{{ data.type }}</div>
			</div>
		</div>
		<div class="card-description">
			{{ data.description }}
		</div>
	</div>
</template>

<style scoped>
.card-header {
	display: flex;
	justify-content: space-evenly;
	align-items: center;
}

.card {
	display: flex;
	flex-direction: column;
	justify-content: space-around;
	border-radius: 15px;
	width: 13vw;
	height: fit-content;
	border: 1px solid #000;
	background-color: #fff;
	box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
	padding: 10px;
	gap: 30px;
}

.card-image {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100px;
}

.card-description {
	height: 60px;
}
</style>