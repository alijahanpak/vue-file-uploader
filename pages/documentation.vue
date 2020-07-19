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
      ['Install', 540],
      ['Setup', 1275],
    ],
    props: [
      ['documentAttachment', 2490],
      ['fileUploaderType', 3200],
      ['cardType', 3960],
      ['fileAccept', 4450],
      ['imageCompressor', 4865],
      ['imageCompressLevel', 5480],
      ['maxFileSize', 5870],
      ['maxFileCount', 6480],
      ['thumb', 7350],
      ['tableThumbColumn', 7760],
      ['tableFixedHeader', 8120],
      ['tableHeight', 8500],
      ['badgeCounter', 8930],
      ['rtlSupport', 9310],
      ['lang', 9700],
      ['btnColor', 10120],
      ['changeFileName', 10120],
      ['addFileDescription', 10120],
      ['addFileTag', 10120],
      ['tags', 10120],
      ['cols', 10120],
    ],
    examples: [
      ['Thumbnail', 11250],
      ['Simple', 12240],
      ['Table', 13150]
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
