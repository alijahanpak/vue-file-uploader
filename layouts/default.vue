<template>
  <v-app>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-btn
        icon
        @click.stop="fixed = !fixed"
      >
        <v-icon v-if="!themeMod" @click="changeThemeMod">mdi-white-balance-sunny</v-icon>
        <v-icon v-else @click="changeThemeMod">mdi-weather-night </v-icon>
      </v-btn>
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn small to="/documentation" text>
        Documentation
      </v-btn>

      <v-btn small to="/" text>
        Examples
      </v-btn>

      <v-btn small href="https://github.com/alijahanpak/handy-uploader" target="_blank" text>
        <v-icon>mdi-github</v-icon> Github
      </v-btn>

    </v-app-bar>
    <v-content>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }} - MIT License</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      themeMod: false,
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Handy Uploader'
    }
  },
  methods: {
    changeThemeMod (){
      this.themeMod = !this.themeMod;
      this.$vuetify.theme.dark= this.themeMod;
    }
  },
}
</script>
