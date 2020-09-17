<template>
    <v-container>
        <v-row>
            <v-card class="my-1 mx-1" v-for="character in characters.results" :key="character.results" max-height="500px" max-width="250px" color="indigo">
                <v-card-title>
                    {{character.name}}
                </v-card-title>
                <v-card-text>
                    <p>Height: {{character.height}} </p>
                    <p>Mass: {{character.mass}} </p>
                    <p v-if="character.hair_color != 'n/a' && character.hair_color != 'none'">Hair color: {{character.hair_color}} </p>
                    <p v-else> This character has no hair </p>
                    <p> Skin color: {{character.skin_color}} </p>
                </v-card-text>
                <div v-if="character.gender == 'male' ">
                <v-chip class="ma-2" color="primary">{{character.gender}}</v-chip>
                </div>
                <div v-else-if="character.gender == 'female'">
                    <v-chip class="ma-2" color="pink">{{character.gender}}</v-chip>
                </div>
                <div v-else>
                    <v-chip class="ma-2">?</v-chip>
                </div>
            </v-card>
        </v-row>
    </v-container> 
</template>

<script>
const baseURL = 'https://swapi.dev/api/people/'
export default {
    data: () => ({
        characters: [],
        error: Boolean,
    }),
    async created() {
             let response = await fetch(baseURL);
            if (response.ok) {
                this.characters = await response.json();
            } else {
                this.error = true;
            }

    }
}
</script>