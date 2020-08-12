<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-toolbar-title>Explore GitHub Repositories with Vue.js</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/ykws/vue-github-explore"
        target="_blank"
        text
      >
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Explore />
    </v-main>
  </v-app>
</template>

<script>
import Explore from './components/Explore';

export default {
  name: 'App',

  components: {
    Explore,
  }
};
</script>
