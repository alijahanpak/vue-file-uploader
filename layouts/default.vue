<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      color="white"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="clipped = !clipped"
      >
        <v-icon>mdi-application</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="fixed = !fixed"
      >
        <v-icon v-if="!themeMod" @click="changeThemeMod">mdi-white-balance-sunny</v-icon>
        <v-icon v-else @click="changeThemeMod">mdi-weather-night </v-icon>
      </v-btn>
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn text>
        Documentation
      </v-btn>

      <v-btn link="https://github.com/alijahanpak/vue-file-uploader" text>
        Github
      </v-btn>

    </v-app-bar>
    <v-content>
      <v-container>
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
      items: [
        {
          icon: 'mdi-image-plus',
          title: 'Thumbnail File uploader',
          to: '/'
        },
        {
          icon: 'mdi-file-upload',
          title: 'Simple File Uploader',
          to: '/simple'
        },
        {
          icon: 'mdi-table',
          title: 'Table File Uploader',
          to: '/table'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'vue-file-uploader'
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
