<template>
    <v-container>
        <v-row>
            <v-card class="my-1 mx-1" v-for="film in films.results" :key="film.results" max-width="350px" color="indigo">
                <v-card-title>
                    {{film.title}}
                </v-card-title>
                <v-card-text>
                    <p>Director: {{film.director}} </p>
                    <p>Release Date: {{film.release_date}} </p>
                    <p>Opening: {{film.opening_crawl}}</p>
                    <!-- <p>Diameter: {{film.diameter}} </p>
                    <p>Climate: {{film.climate}}  </p> -->
                </v-card-text>
            </v-card>
        </v-row>
    </v-container> 
</template>

<script>
const baseURL = 'https://swapi.dev/api/films/'
export default {
    data: () => ({
    films: [],
        error: Boolean,
    }),
    methods: {
        async callForApi() {
            let response = await fetch(baseURL);
            if (response.ok) {
                this.films = await response.json();
            } else {
                this.error = true;
            }
        },
    },
    async created() {
            let response = await fetch(baseURL);
            if (response.ok) {
                this.films = await response.json();
            } else {
                this.error = true;
            }
    }
}
</script>