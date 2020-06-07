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
          :setDocumentAttachment="setInsertedFile"
          v-model:documentAttachment="registryDocFile"
          :state="'INSERT'"
          :maxFileSize.sync= "maxFileSizeChange"
          :imageCompressor.sync= "imageCompressorState"
          :imageCompressLevel.sync= "imageCompressLevelChange"
          :fileUploaderType= "'thumbnail'"
          :maxFileCount.sync="maxFileCountChange"
          :cardType.sync= "cardType"
          :badgeCounter.sync= "badgeCounterState"
          ref="fileUploader"
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
          <v-container>
            <v-row>
              <v-col cols="12" md="12" xs="12">
                <p>Select card type: </p>
                <v-chip-group
                  v-model="selectedCardType"
                  active-class="deep-purple accent-4 white--text"
                  column
                >
                  <v-chip>DEFAULT</v-chip>

                  <v-chip>OUTLINED</v-chip>

                  <v-chip>RAISED</v-chip>

                  <v-chip>SHAPED</v-chip>

                  <v-chip>TILE</v-chip>
                </v-chip-group>
              </v-col>
              <v-col cols="12" md="6" xs="12">
                <v-text-field
                  v-model="maxFileCountChange"
                  label="Maximum file count"
                >
                </v-text-field>
              </v-col>
              <v-col cols="12" md="6" xs="12">
                <v-text-field
                  v-model="maxFileSizeChange"
                  label="Maximum file size (KB)"
                >
                </v-text-field>
              </v-col>
              <v-col cols="3" md="3" xs="12">
                <v-switch
                  v-model="imageCompressorState"
                  :label="`Image compressor: ${imageCompressorState.toString()}`"
                ></v-switch>
              </v-col>
              <v-col cols="9" md="9" xs="12">
                <v-slider style="margin-top: 16px;"
                  :disabled="!imageCompressorState"
                  v-model="imageCompressLevelChange"
                  label="Image compress level"
                  persistent-hint
                  max="1"
                  step="0.1"
                  thumb-label="always"
                  ticks
                ></v-slider>
              </v-col>
              <v-col cols="12" md="12" xs="12">
                <v-switch
                  v-model="badgeCounterState"
                  :label="`Badge Counter: ${badgeCounterState.toString()}`"
                ></v-switch>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1"
            text
            @click="optionDialog = false"
          >
            ok
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
    selectedCardType: 0,
    cardType: '',
    badgeCounterState: true,
    maxFileCountChange: 5,
    maxFileSizeChange: 5120,
    imageCompressorState: true,
    imageCompressLevelChange: 0.5,
  }),
  watch: {
    selectedCardType: function (val) {
      this.setCardType()
    },
    badgeCounterState : function (val) {
        this.badgeCounter = this.badgeCounterState;
    },
    maxFileCountChange : function (val) {
        this.maxFileCount = this.maxFileCountChange;
    },
    maxFileSizeChange : function (val) {
        this.maxFileSize = Number(this.maxFileSizeChange);
    },
    imageCompressorState : function (val) {
      this.imageCompressor = this.imageCompressorState;
    },
    imageCompressLevelChange : function (val) {
      this.imageCompressLevel = this.imageCompressLevelChange;
    },
  },
  methods:{
    setInsertedFile(item){
      this.registryDocFile = item;
    },
    openOptions() {

    },

    setCardType(){
      switch (this.selectedCardType) {
        case 0 :
          this.cardType = 'default'
          break;
        case 1 :
          this.cardType = 'outlined'
          break;
        case 2 :
          this.cardType = 'raised'
          break;
        case 3 :
          this.cardType = 'shaped'
          break;
        case 4 :
          this.cardType = 'tile'
          break;
      }
      //this.$refs.fileUploader.setCardTheme();
    },
  },
}
</script>
