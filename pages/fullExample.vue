<template>
  <v-container>
    <v-row>
      <v-col>
        <file-uploader
          :setDocumentAttachment="setRegistryDocFile"
          v-model:documentAttachment="registryDocFile"
          :state="'INSERT'"
          :maxFileSize= "12120"
          :thumbnail= "true"
          ref="registryDocForm"
        >
        </file-uploader>
      </v-col>
    </v-row>
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
  }),


  setRegistryDocFile(item){
    this.registryDocFile = item;
  },
}
</script>
