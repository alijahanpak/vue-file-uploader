<template>
  <v-container fluid>
    <v-row>
        <v-navigation-drawer
          fixed
          app
          width="300"
        >
          <v-list expand>
              <v-list-group
                no-action
                sub-group
                value="true"
              >
                <template v-slot:activator>
                  <v-list-item-content>
                    <v-list-item-title>Getting Started</v-list-item-title>
                  </v-list-item-content>
                </template>

                <v-list-item
                  v-for="(gs, i) in gettingStart"
                  :key="i"
                  link
                >
                  <v-list-item-title style="font-size: 0.9em" @click="$vuetify.goTo(gs[1])" v-text="gs[0]"></v-list-item-title>
                </v-list-item>
            </v-list-group>

            <v-list-group
              sub-group
              no-action
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>Props</v-list-item-title>
                </v-list-item-content>
              </template>
              <v-list-item
                v-for="(prop, i) in props"
                :key="i"
                link
              >
                <v-list-item-title style="font-size: 0.9em" @click="$vuetify.goTo(prop[1])" v-text="prop[0]"></v-list-item-title>
              </v-list-item>
            </v-list-group>

            <v-list-group
              sub-group
              no-action
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>Refs</v-list-item-title>
                </v-list-item-content>
              </template>
              <v-list-item
                v-for="(ref, i) in refs"
                :key="i"
                link
              >
                <v-list-item-title style="font-size: 0.9em" @click="$vuetify.goTo(ref[1])" v-text="ref[0]"></v-list-item-title>
              </v-list-item>
            </v-list-group>

            <v-list-group
              sub-group
              no-action
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>Code Examples</v-list-item-title>
                </v-list-item-content>
              </template>
              <v-list-item
                v-for="(example, i) in examples"
                :key="i"
                link
              >
                <v-list-item-title style="font-size: 0.9em" @click="$vuetify.goTo(example[1])" v-text="example[0]"></v-list-item-title>
              </v-list-item>
            </v-list-group>
          </v-list>
        </v-navigation-drawer>
      <v-col cols="12" lg="12" md="12" xs="12">
        <p class="header">Getting Started</p>
        <v-divider></v-divider>
        <v-row>
          <v-col cols="12" lg="12" md="12" xs="12">
            <template>
              <div v-html="readme"></div>
            </template>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import readme from './README.md'
export default {
  data: () => ({
    panelHeight: 0,
    gettingStart: [
      ['Install', 250],
      ['Setup', 350],
    ],
    props: [
      ['documentAttachment', 620],
      ['fileUploaderType', 1180],
      ['fileAccept', 1180],
      ['imageCompressor', 1970],
      ['imageCompressLevel', 1150],
      ['maxFileSize', 1150],
      ['maxFileCount', 1150],
      ['thumb', 1150],
      ['tableThumbColumn', 1150],
      ['tableFixedHeader', 1150],
      ['tableHeight', 1150],
      ['badgeCounter', 1150],
      ['rtlSupport', 1150],
      ['lang', 1150],
    ],
    refs: [
      ['fileUploader', 1150]
    ],
    examples: [
      ['Thumbnail', 1150],
      ['Simple', 1150],
      ['Table', 1150]
    ],
  }),
  computed: {
    readme() {
      return readme
    }
  },
  watch: {

  },
  mounted() {
    this.onResize();
  },
  methods:{
    onResize () {
      window.addEventListener('resize', this.onResize);
      this.panelHeight = window.innerHeight - 150;
    },
    scrollWin (location){
      window.scrollTo(0, location)
    }
  },
}
</script>
<style scoped>
  .header{
    color: #263238;
    font-size: 2rem;
  }
  .title{
    margin: 15px;
    color: #263238;
    font-size: 1.5rem;
  }
  .sub-link{
    margin-left: 10px;
  }
  code{
    box-shadow: none !important;
  }
  .x-btn-inner {
    text-transform: none !important;
  }
</style>
