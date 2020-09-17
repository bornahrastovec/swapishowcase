<template>
    <v-container>
        <v-row>
            <v-card class="my-1 mx-1" v-for="planet in planets.results" :key="planet.results" max-height="500px" max-width="250px" color="indigo">
                <v-card-title>
                    {{planet.name}}
                </v-card-title>
                <v-card-text>
                    <p>Population: {{planet.population}} </p>
                    <p>Orbital period: {{planet.orbital_period}} </p>
                    <p>Gravity: {{planet.gravity}}</p>
                    <p>Diameter: {{planet.diameter}} </p>
                    <p>Climate: {{planet.climate}}  </p>
                </v-card-text>
            </v-card>
        </v-row>

    </v-container> 
</template>

<script>
const baseURL = 'https://swapi.dev/api/planets/'
export default {
    data: () => ({
        planets: [],
        error: Boolean,
    }),
    async created() {
                    let response = await fetch(baseURL);
            if (response.ok) {
                this.planets = await response.json();
            } else {
                this.error = true;
            }

    }
}
</script>