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
      ['Install', 460],
      ['Setup', 655],
    ],
    props: [
      ['documentAttachment', 920],
      ['fileUploaderType', 1830],
      ['cardType', 2610],
      ['fileAccept', 3060],
      ['imageCompressor', 3500],
      ['imageCompressLevel', 4100],
      ['maxFileSize', 4480],
      ['maxFileCount', 5050],
      ['thumb', 5680],
      ['tableThumbColumn', 6070],
      ['tableFixedHeader', 6470],
      ['tableHeight', 6850],
      ['badgeCounter', 7250],
      ['rtlSupport', 7640],
      ['lang', 8020],
      ['btnColor', 8465],
    ],
    refs: [
      ['fileUploader', 8850]
    ],
    examples: [
      ['Thumbnail', 9600],
      ['Simple', 10400],
      ['Table', 11180]
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
