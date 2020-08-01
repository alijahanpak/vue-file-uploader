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
      ['Setup', 1330],
    ],
    props: [
      ['documentAttachment', 2490],
      ['fileUploaderType', 3250],
      ['cardType', 4000],
      ['fileAccept', 4430],
      ['imageCompressor', 4850],
      ['imageCompressLevel', 5270],
      ['maxFileSize', 5660],
      ['maxFileCount', 6035],
      ['thumb', 6470],
      ['tableThumbColumn', 6860],
      ['tableFixedHeader', 7250],
      ['tableHeight', 7630],
      ['badgeCounter', 8020],
      ['rtlSupport', 8410],
      ['lang', 8800],
      ['customLang', 9200],
      ['btnColor', 10540],
      ['changeFileName', 10920],
      ['addFileDescription', 11310],
      ['addFileTag', 11700],
      ['tags', 12070],
      ['cols', 12450],
    ],
    examples: [
      ['Thumbnail', 12830],
      ['Simple', 13680],
      ['Table', 14500]
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
