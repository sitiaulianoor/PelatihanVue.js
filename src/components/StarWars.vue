<template>
	<div class="star-wars">
		<div class="star-wars-form">
			<table>
				<tr>
					<td>Name</td>
					<td><input v-model="newCharacter.name"/></td>
				</tr>
				<tr>
					<td>Height</td>
					<td><input v-model="newCharacter.height"/></td>
				</tr>
				<tr>
					<td>Mass</td>
					<td><input v-model="newCharacter.mass"/></td>
				</tr>
				<tr>
					<td>Gender</td>
					<td>
						<select v-model="newCharacter.gender">
							<option value="0">Male</option>
							<option value="1">Female</option>
						</select>
					</td>
				</tr>
				<tr>
					<td></td>
					<td><button @click="addChar">Add</button></td>
				</tr>
			</table>
		</div>
		<p v-if="isLoading">Loading...</p>
		<div v-if="!isLoading" class="star-wars-list">
			<table>
				<tr v-for="(char, id) in characters" :key="id">
					<td>{{char.name}}</td>
					<td>{{char.height}} cm</td>
					<td>{{char.mass}} kg</td>
					<td>{{char.gender == 0 ? "Male" : "Female"}}</td>
				</tr>
			</table>
		</div>
	</div>
</template>

<script>
export default{
	name : "StarWars",
	data() {
		return{
			characters: [],
			newCharacter:{
				name: "",
				height: 0,
				mass: 0,
				gender: 0
			},
			isLoading: true,
		}
	},

	mounted(){

		fetch("https://swapi.co/api/people")
		.then(response => response.json())
		.then(res => {
			this.isLoading = false;
			this.characters = res.results
		})
	},
	
	methods: {
		addChar(){
			this.characters.push(this.newCharacter);
			this.newCharacter = {
				name: "",
				height: 0,
				mass: 0,
				gender: 0
			}
		}
	}
}
	
</script>