<template>
  <v-container>
    <v-row>
      <v-col cols="12" lg="12" md="12" xs="12">
        <div class="text-center">
          <v-icon
            color="green accent-4"
            size="200"
          >
            mdi-cloud-upload-outline
          </v-icon>
          <p style="color: #424242; font-size: 3rem">Vue File Uploader</p>
          <p style="color: #757575; font-size: 1.5rem">Complete and easy file uploader in Vue.js</p>
        </div>
        <v-col cols="12" lg="12" md="12" xs="12">
          <div class="text-center ma-2">
            <v-chip
              large
              class="ma-2"
              color="green darken-1"
              label
              text-color="white"
              @click="optionDialog = true"
              to="/thumbnail"
            >
              <v-icon left>mdi-image-plus</v-icon>
              Thumbnail File Uploader
            </v-chip>

            <v-chip
              large
              class="ma-2"
              color="green darken-1"
              label
              text-color="white"
              @click="optionDialog = true"
              to="/simple"
            >
              <v-icon left>mdi-file-upload</v-icon>
              Simple File Uploader
            </v-chip>

            <v-chip
              large
              class="ma-2 text-center"
              color="green darken-1"
              label
              text-color="white"
              @click="optionDialog = true"
            >
              <v-icon left>mdi-table</v-icon>
              Table File Uploader
            </v-chip>
          </div>
        </v-col>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  components: {
  },
  data: () => ({

  }),
  methods:{

  },
}
</script>
