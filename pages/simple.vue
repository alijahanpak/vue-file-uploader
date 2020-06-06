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
          :fileUploaderType= "'simple'"
          :maxFileCount="5"
          :cardType="'outline'"
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
        <v-card-title class="headline">You can customize your File-Uploader</v-card-title>

        <v-card-text>
          <p>Fil uploader type: </p>
          <v-chip-group
            v-model="fileUploaderTypeSelect"
            active-class="deep-purple accent-4 white--text"
            column
          >
            <v-chip @click="fileUploadertype = 'thumbnail'">File explorer - with thumbnail</v-chip>

            <v-chip @click="fileUploadertype = 'fileExplorer'">File Explorer - Simple</v-chip>

            <v-chip @click="fileUploadertype = 'table'">Table</v-chip>

          </v-chip-group>
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
    fileUploaderTypeSelect: 0,
    fileUploaderType: 'thumbnail',
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
