<template>
  <v-container>
    <v-row>
      <v-col cols="12" lg="12" md="12" xs="12">
        <v-chip
          class="ma-2"
          color="pink"
          label
          text-color="white"
          @click="optionDialog = true"
        >
          <v-icon left>mdi-cog-outline</v-icon>
          Options
        </v-chip>
      </v-col>
      <v-col cols="12" lg="12" md="12" xs="12">
        <file-uploader
          :setDocumentAttachment="setRegistryDocFile"
          v-model:documentAttachment="registryDocFile"
          :state="'INSERT'"
          :maxFileSize= "12120"
          :fileUploaderType= "'thumbnail'"
          :maxFileCount="5"
          :cardType= "'outline'"
          :badgeCounter= "true"
          ref="registryDocForm"
        >
        </file-uploader>
      </v-col>
    </v-row>
    <!---------------------File Uploader Options------------------------------->
    <v-dialog
      v-model="optionDialog"
      max-width="80%"
    >
      <v-card>
        <v-card-title class="headline">You can customize your Thumbnail File Uploader</v-card-title>

        <v-card-text>
          <p>Maximum file upload: </p>
          <v-text-field>
            label="Maximum file upload"
          </v-text-field>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            Disagree
          </v-btn>

          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            Agree
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <!---------------------File Uploader Options------------------------------->
  </v-container>
</template>

<script>
import fileUploader from '~/components/fileUploader';
export default {
  components: {
    fileUploader,
  },
  data: () => ({
    registryDocFile: [],
    optionDialog: false,
  }),
  methods:{
    setRegistryDocFile(item){
      this.registryDocFile = item;
    },
    openOptions() {

    }
  },
}
</script>
