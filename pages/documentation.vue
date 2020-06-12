<template>
  <v-container fluid>
    <v-row>
      <v-col style="overflow: auto;border-right: 1px solid #E0E0E0" :style="{height: panelHeight+'px'}" cols="12" lg="2" md="2" xs="12">
        <v-btn text small>overview</v-btn><br>
        <v-btn text small>Getting Started</v-btn><br>
        <v-btn class="sub-link" text small color="grey darken-2">Install</v-btn><br>
        <v-btn class="sub-link" text small color="grey darken-2">setup</v-btn><br>
        <v-btn text small>props</v-btn><br>
        <v-btn @click="$vuetify.goTo(600)" class="sub-link" text small color="grey darken-2">documentAttachment</v-btn><br>
        <v-btn @click="$vuetify.goTo(1150)" class="sub-link" text small color="grey darken-2">fileUploaderType</v-btn><br>
        <v-btn class="sub-link" text small color="grey darken-2">maxFileSize</v-btn><br>
      </v-col>
      <v-col style="overflow: auto;" :style="{height: panelHeight+'px'}" cols="12" lg="10" md="10" xs="12">
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
  code{
    box-shadow: none !important;
  }
</style>
