<template>
  <v-container fluid>
    <v-row>
      <v-col style="overflow: auto;border-right: 1px solid #E0E0E0" :style="{height: panelHeight+'px'}" cols="12" lg="2" md="2" xs="12">
        <v-btn text small>Getting Started</v-btn>
        <v-btn class="sub-link" text small>NPM</v-btn>
      </v-col>
      <v-col cols="12" lg="10" md="10" xs="12">
        <p class="header">Getting Started</p>
        <v-divider></v-divider>
        <p class="title">Install</p>
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
    items: [
      { title: 'Getting Started'},
      { title: 'NPM', },
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
</style>
