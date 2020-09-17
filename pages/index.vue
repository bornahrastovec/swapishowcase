<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <v-card>
        <v-card-title class="headline">
          Star Wars API manipulator
        </v-card-title>
        <v-card-text>
          <p>
            This website was created as a sample project using Nuxt.js just for practice and education purposes. <br/>
            I hope you have fun with this app, and I hope it will motivate you to start learning Vue. <br/>
            The UI framework I used was Vuetify for its material design. It makes stuff look modern
          </p>
          <hr />
          <blockquote>Creator</blockquote>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>

export default {
  data: () => ({
      hello: '',
      description: '',
      someFiles: [],
      rules: [
        value => !!value || 'Required.',
        value => (value && value.length >= 3) || 'Min 3 characters',
      ],
    }),
  components: {
  },
}
</script>
