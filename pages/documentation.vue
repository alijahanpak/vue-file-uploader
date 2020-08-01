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
    <v-fab-transition>
      <v-btn
        v-scroll="onScroll"
        v-show="showScrollToTop"
        fab
        dark
        fixed
        bottom
        right
        color="primary"
        @click="$vuetify.goTo(0)"
      >
        <v-icon>mdi-chevron-up</v-icon>
      </v-btn>
    </v-fab-transition>
  </v-container>
</template>

<script>
import readme from './README.md'
export default {
  data: () => ({
    panelHeight: 0,
    offsetTop: 0,
    gettingStart: [
      ['Install', 625],
      ['Setup', 1260],
    ],
    props: [
      ['documentAttachment', 2430],
      ['fileUploaderType', 3210],
      ['cardType', 3950],
      ['fileAccept', 4360],
      ['imageCompressor', 4750],
      ['imageCompressLevel', 5120],
      ['maxFileSize', 5530],
      ['maxFileCount', 5890],
      ['thumb', 6310],
      ['tableThumbColumn', 6680],
      ['tableFixedHeader', 7060],
      ['tableHeight', 7420],
      ['badgeCounter', 7810],
      ['rtlSupport', 8180],
      ['lang', 8550],
      ['customLang', 8960],
      ['btnColor', 10410],
      ['changeFileName', 10780],
      ['addFileDescription', 11160],
      ['addFileTag', 11540],
      ['tags', 11900],
      ['cols', 12260],
    ],
    examples: [
      ['Thumbnail', 12620],
      ['Simple', 13510],
      ['Table', 14400]
    ],
  }),
  computed: {
    readme() {
      return readme
    },
    showScrollToTop() {
      return this.offsetTop > 60;
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
    onScroll() {
      this.offsetTop = window.pageYOffset || document.documentElement.scrollTop;
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
