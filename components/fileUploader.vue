<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="12" xs="12" class="BYekan">
        <v-btn v-if="state === 'INSERT'" color="info" @click="openInputDocumentModal"> Insert File </v-btn>
        <v-btn v-else color="info" @click="openInputDocumentModal">Insert File</v-btn>
        <v-row v-if="!thumbnail">
          <v-col v-for="(attachment, index) in _documentAttachment" :key="attachment.id" cols="12" md="4" xs="12">
            <v-hover>
              <template v-slot:default="{ hover }">
                <v-card outlined>
                  <v-list-item three-line>
                    <v-list-item-content>
                      <v-list-item-subtitle color="blue-grey darken-3">{{attachment.file.name}}</v-list-item-subtitle>
                      <v-list-item-subtitle v-if="Number((attachment.file.size / 1000).toFixed(1)) < 1024 ">
                        <v-chip
                          color="teal lighten-2"
                          label
                          text-color="white"
                        >
                          {{  Number((attachment.file.size / 1000).toFixed(1)) + 'KB'}}
                          <v-icon right>mdi-harddisk</v-icon>
                        </v-chip>
                      </v-list-item-subtitle>
                      <v-list-item-subtitle v-if="Number((attachment.file.size / 1000).toFixed(1)) > 1024">
                        <v-chip
                          color="teal lighten-2"
                          label
                          text-color="white"
                        >
                          {{  Number(((attachment.file.size / 1000) / 1024 ).toFixed(1)) + ' MB'}}
                          <v-icon right>mdi-harddisk</v-icon>
                        </v-chip>
                      </v-list-item-subtitle>
                    </v-list-item-content>
                    <v-list-item-avatar
                      tile
                      size="80"
                      color="blue-grey lighten-5"
                    >
                      <template>
                        <v-icon  v-if="attachment.file.name.split('.').pop().toLowerCase() == 'pdf'" x-large file-word-outline color="red darken-1">mdi-file-pdf-outline</v-icon>
                        <v-icon  v-else-if="attachment.file.name.split('.').pop().toLowerCase() == 'doc' || attachment.file.name.split('.').pop().toLowerCase() == 'docx' || attachment.file.name.split('.').pop().toLowerCase() == 'odt'" x-large file-word-outline color="blue darken-1">mdi-file-word-outline</v-icon>
                        <v-icon  v-else-if="attachment.file.name.split('.').pop().toLowerCase() == 'jpg' || attachment.file.name.split('.').pop().toLowerCase() == 'jpeg' || attachment.file.name.split('.').pop().toLowerCase() == 'png' || attachment.file.name.split('.').pop().toLowerCase() == 'tif' || attachment.file.name.split('.').pop().toLowerCase() == 'bmp'" x-large file-word-outline color="deep-purple darken-1">mdi-file-image-outline</v-icon>
                        <v-icon  v-else-if="attachment.file.name.split('.').pop().toLowerCase() == 'xls' || attachment.file.name.split('.').pop().toLowerCase() == 'xlsx'" x-large file-word-outline color="teal darken-1">mdi-file-excel-outline</v-icon>
                        <v-icon  v-else-if="attachment.file.name.split('.').pop().toLowerCase() == 'mp4' || attachment.file.name.split('.').pop().toLowerCase() == 'mov' || attachment.file.name.split('.').pop().toLowerCase() == 'flv' || attachment.file.name.split('.').pop().toLowerCase() == 'wmv' || attachment.file.name.split('.').pop().toLowerCase() == 'avi'" x-large file-word-outline color="red lighten-1">mdi-file-video-outline</v-icon>
                        <v-icon  v-else-if="attachment.file.name.split('.').pop().toLowerCase() == 'dwg' " x-large file-word-outline color="indigo lighten-2">mdi-file-cad</v-icon>
                        <v-icon  v-else-if="attachment.file.name.split('.').pop().toLowerCase() == 'zip' || attachment.file.name.split('.').pop().toLowerCase() == 'rar' || attachment.file.name.split('.').pop().toLowerCase() == '7-zip'   " x-large file-word-outline color="lime lighten-1">mdi-folder-zip-outline</v-icon>
                        <v-icon  v-else-if="attachment.file.name.split('.').pop().toLowerCase() == 'txt' " x-large file-word-outline color="light-green darken-3">mdi-script-text-outline</v-icon>
                        <v-icon  v-else x-large file-word-outline color="indigo lighten-1">mdi-file-question-outline</v-icon>
                      </template>
                    </v-list-item-avatar>
                  </v-list-item>
                  <v-fade-transition>
                    <v-overlay
                      v-if="hover"
                      absolute
                      color="#036358"
                    >
                      <template v-if="state === 'INSERT'">
                        <v-tooltip right>
                          <template v-slot:activator="{ on }">
                            <v-btn outlined large fab v-on="on"  @click="openDeleteDialog(index , '')"><v-icon color="red">mdi-trash-can-outline</v-icon></v-btn>
                          </template>
                          <span class="BYekan">Delete</span>
                        </v-tooltip>
                      </template>
                      <template v-else>
                        <v-tooltip right>
                          <template v-slot:activator="{ on }">
                            <v-btn outlined large fab v-on="on"  @click="openDeleteDialog(index, attachment.ID)"><v-icon color="red">mdi-trash-can-outline</v-icon></v-btn>
                          </template>
                          <span class="BYekan">Delete</span>
                        </v-tooltip>
                        <v-tooltip left>
                          <template v-slot:activator="{ on }">
                            <v-btn style="margin-right: 20px" outlined large fab v-on="on" color="purple lighten-5" @click="getBinaryFile(attachment)" target="_blank"><v-icon>mdi-eye-check-outline</v-icon></v-btn>
                          </template>
                          <span class="BYekan">Preview</span>
                        </v-tooltip>
                      </template>
                    </v-overlay>
                  </v-fade-transition>
                </v-card>
              </template>
            </v-hover>
          </v-col>
        </v-row>
        <v-row v-if="thumbnail">
          <v-col v-for="(attachment, index) in _documentAttachment" :key="attachment.id" cols="12" md="4" xs="12">
            <v-card
              class="mx-auto"
              max-width="344"
            >
              <v-img
                :src="'data:'+ attachment.file.format  + ',' + attachment.file.binary "
                height="200px"
              ></v-img>

              <v-card-subtitle>
                {{attachment.file.name}}
              </v-card-subtitle>
              <v-card-subtitle v-if="Number((attachment.file.size / 1000).toFixed(1)) < 1024" class="mt2">
                <v-chip
                  color="teal lighten-2"
                  label
                  text-color="white"
                >
                  {{  Number((attachment.file.size / 1000).toFixed(1)) + 'KB'}}
                  <v-icon right>mdi-harddisk</v-icon>
                </v-chip>
              </v-card-subtitle>
              <v-card-subtitle v-if="Number((attachment.file.size / 1000).toFixed(1)) > 1024">
                <v-chip
                  color="teal lighten-2"
                  label
                  text-color="white"
                >
                  {{  Number(((attachment.file.size / 1000) / 1024 ).toFixed(1)) + ' MB'}}
                  <v-icon right>mdi-harddisk</v-icon>
                </v-chip>
              </v-card-subtitle>
              <v-card-actions>
                <v-btn text @click="openDeleteDialog(index , '')" >Delete</v-btn>
                <v-spacer></v-spacer>

              </v-card-actions>

            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
    <!--Insert New Document Dialog Start-->
    <v-row justify="center">
      <v-dialog v-model="insertDocumentDialog" :scrollable="false" persistent width="50%">
        <v-card>
          <v-card-title>
            <v-icon @click="insertDocumentDialog = false">mdi-close</v-icon>
          </v-card-title>
          <v-card-text class="BYekan">
            <v-file-input multiple show-size v-model="tempAttachment" label="Insert New File"></v-file-input>
          </v-card-text>
          <v-card-actions>
            <v-btn class="BYekan" :disabled="tempAttachment == null || btnLoader" :loading="btnLoader" color="info" @click="uploadFieldChange">Add</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
    <!--Insert New Document Dialog End--------------------------------------------------------------->
    <!--File Uploader SnackBar Alert Start --------------------------------------------------------------->
    <v-snackbar class="BYekan"
      v-model="fileUploaderSnackBarAlert"
      right
      bottom
      :color="fileUploaderSnackBarAlertColor"
      :timeout="3000"
    >
      {{fileUploaderSnackText}}
      <v-btn
        color="white"
        text
        @click="fileUploaderSnackBarAlert = false"
      >
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </v-snackbar>
    <!--File Uploader SnackBar Alert Start -->
    <!--DELETE Building Dialog End----------------------------------------------------------START---->
    <v-row justify="center">
      <v-dialog v-model="deleteDocumentDialog" persistent width="30%">
        <v-card>
          <v-card-title>
            <v-icon color="red"></v-icon>
          </v-card-title>
          <v-card-text class="BYekan">
            Are you sure you want to delete the file?
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn class="BYekan" color="green darken-1" text @click="deleteDocumentDialog= false">Cancel</v-btn>
            <v-btn class="BYekan" color="primary" :disabled="btnLoader" :loading="btnLoader" @click="deleteDocument">Delete </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
    <!--DELETE Building Dialog End----------------------------------------------------------------END---->
  </v-container>
</template>

<script>
  /**
   * This is an example of uploading files. with this component you can see, insert, delete files.
   * @version 1.0
   * @author [ali jahanpak](https://github.com/alijahanpak)
   * @since Version 1.0
   */
  export default {
    props: {
      /**
       * get recordID from selected record
       */
      recordID: Number,
      /**
       * Array contain files
       */
      documentAttachment: [Array],
      /**
       * define 'INSERT' or 'UPDATE' mode
       */
      state: String,
      /**
       * Send api url for 'add' and 'delete'.
       * f.e: /building/add or /building/delete
       */
      apiUrl: String,
      /**
       * Send api url for fetch current record after changes.
       * f.e: /building/fetch.
       */
      apiFetchUrl: String,
      /**
       * Send caption Id to define id property to UPDATE apt
       */
      captionId: String,
      /**
       * Send insertFilePermission String for manage user permission
       */
      insertFilePermission: String,
      /**
       * Send deleteFilePermission String for manage user permission
       */
      deleteFilePermission: String,
      /**
       * Set Maximum File Size in KB
       */
      maxFileSize: {
        type: Number,
        Default: 5120,
      },
      /**
       * Enable/Disable thumbnail for File Explore
       */
      thumbnail: Boolean

    },
    model: {
      prop: 'documentAttachment',
      event: 'documentAttachmentChange'
    },
    data: () => ({
      insertDocumentDialog: false,
      deleteDocumentDialog: false,
      tempAttachment:[],
      fileUploaderSnackBarAlert: false,
      fileUploaderSnackText: '',
      fileUploaderSnackBarAlertColor: 'green',
      readerFile: null,
      registryDocFile: [],
      documentAttachmentAPI: [],
      btnLoader: false,
      hover: '',
      selectedIndex: '',
      selectedId: '',
      returnedRecord: {},
    }),
    watch: {

    },
    computed: {
      _documentAttachment: {
        get: function() {
          return this.documentAttachment
        },
        set: function(value) {
          this.$emit('documentAttachmentChange', value)
        }
      },
    },
    mounted () {

    },
    created(){

    },
    destroyed(){
      this.registryDocFile= [];
    },
    methods: {
      openInputDocumentModal(){
        this.btnLoader= false;
        this.tempAttachment= [];
        this.insertDocumentDialog = true;
      },

      handleUpload(fileAttachment) {
          let reader = new FileReader();
          return new Promise(function(resolve, reject) {
            reader.onloadend = () => {
              resolve(reader.result);
            };
            reader.readAsDataURL(fileAttachment);
          });
      },

    /**
     * asynchronous method to insert selected file(s)
     *
     * @public
     * @returns {Array} selected file(s)
     */
      async uploadFieldChange (){
        this.btnLoader= true;
        for(let item of this.tempAttachment){
          if((item.size / 1000).toFixed(1) > this.maxFileSize){
            this.fileUploaderSnackBarAlertColor= 'red';
            this.fileUploaderSnackText= `Max file size is ${Math.round(this.maxFileSize / 1024)} MB`
            this.fileUploaderSnackBarAlert= true;
          }
          else{
            let tempFile= {};
            let file = {};
            try {
              const fileContents = await this.handleUpload(item);
              this.readerFile = fileContents;
            } catch (e) {
            }
            let fullFileType= this.readerFile.split(";");
            let fileType= fullFileType[0].split(":")
            let status = false;
            let imgFile= ''
            let sizeInKb=0;
            if(fileType[1] === "image/png" || fileType[1] === "image/jpg" || fileType[1] === "image/jpeg" || fileType[1] === "application/octet-stream"){
              status = true;
              imgFile = await this.compressImage(this.readerFile, fileType[1]);
            }
            tempFile.subject= item.name;
            let strTemp= this.readerFile.split(",")
            if(status){
              let imgTemp= imgFile.split(",")
              tempFile.binary=imgTemp[1];
              sizeInKb= new Buffer(imgFile, 'base64').length;
              tempFile.size= String(sizeInKb);
            }
            else{
              tempFile.binary=strTemp[1];
              tempFile.size= String(item.size);
            }
            tempFile.name= item.name;
            //tempFile.format= item.name.split('.').pop().toLowerCase();
            tempFile.format= strTemp[0].replace('data:' ,'');
            file.file=tempFile;
            this.registryDocFile.push(file);
            /**
             * Send updated array to parent and show new details
             * this Event call if state = 'INSERT'
             * @property {array} newValue new value set
             */
            console.log(JSON.stringify(this.registryDocFile));
            this.$emit('setDocumentAttachment' , this.registryDocFile);
            this._documentAttachment= this.registryDocFile;
            if(this.state === 'UPDATE')
              this.documentAttachmentAPI.push(file);
          }
        }
        //console.log('FILE =>>>>' +JSON.stringify(this.documentAttachmentAPI));
        if (this.state === 'UPDATE'){
          let apiDATA= [];
          for(let item of this.documentAttachmentAPI){
            let obj = {};
            const newProperty = this.captionId;
            obj[newProperty] =  this.recordID;
            obj.file= item.file;
            apiDATA.push(obj)
          }
          this.$axios.$post(this.apiUrl+ 'add', apiDATA).then((response) => {
            this.fileUploaderSnackText= 'فایل مورد نظر با موفقیت افزوده شد';
            this.fileUploaderSnackBarAlertColor= 'green';
            this.fileUploaderSnackBarAlert= true;
            this.$axios.$post(this.apiFetchUrl,{id: this.recordID})
              .then(response => {
                //this.returnedRecord = response;
                this.btnLoader= false;
                this.$emit('fetchData');
                /**
                 * Send updated record to parent and show new details
                 *
                 * @property {response} newValue new value set
                 */
                this.$emit('getRecordDetail' , response);
                this.insertDocumentDialog= false;
              })
              .catch(error => {
                console.log(error.response)
              });
            console.log(response);
          },(error) => {
            console.log(error);
            this.btnLoader = false;
            this.fileUploaderSnackBarAlertColor = 'red';
            this.fileUploaderSnackText = 'خطا در افزودن فایل! لطفا دوباره تلاش کنید'
            this.fileUploaderSnackBarAlert = true;
          });
        }
        //console.log(JSON.stringify( this.registryDocFile));
        this.documentAttachmentAPI= [];
        this.insertDocumentDialog= false;
      },

      compressImage (base64, fileFormat) {
        const canvas = document.createElement('canvas')
        const img = document.createElement('img')

        return new Promise((resolve, reject) => {
          img.onload = function () {
            let width = img.width
            let height = img.height
            /*const maxHeight = 1250
            const maxWidth = 1250

            if (width > height) {
              if (width > maxWidth) {
                height = Math.round((height *= maxWidth / width))
                width = maxWidth
              }
            } else {
              if (height > maxHeight) {
                width = Math.round((width *= maxHeight / height))
                height = maxHeight
              }
            }*/
            canvas.width = width
            canvas.height = height

            const ctx = canvas.getContext('2d')
            ctx.drawImage(img, 0, 0, width, height)

            resolve(canvas.toDataURL('image/jpeg', 0.3))
          }
          img.onerror = function (err) {
            reject(err)
          }
          img.src = base64
        })
      },

      openDeleteDialog(index , deleteId){
        this.btnLoader = false;
        this.selectedIndex= index;
        this.selectedId= deleteId;
        this.deleteDocumentDialog= true;
      },


       deleteDocument(){
        if(this.state === 'INSERT')
        {
          this.registryDocFile.splice(this.selectedIndex , 1);
          this._documentAttachment= this.registryDocFile;
          this.deleteDocumentDialog= false;
        }
        else if(this.state === 'UPDATE'){
          this.btnLoader= true;
          this.$axios.$post(this.apiUrl+ 'delete', {
            id: this.selectedId
          }).then((response) => {
            this.registryDocFile.splice(this.selectedIndex , 1);
            this._documentAttachment= this.registryDocFile;
            this.fileUploaderSnackText= 'فایل با موفقیت حذف گردید'
            this.fileUploaderSnackBarAlertColor= 'green';
            this.fileUploaderSnackBarAlert= true;
            this.$axios.$post(this.apiFetchUrl,{id: this.recordID})
              .then(response => {
                //this.returnedRecord = response;
                this.btnLoader= false;
                this.$emit('getRecordDetail' ,response);
                this.deleteDocumentDialog= false;
              })
              .catch(error => {
                console.log(error.response)
              });
            console.log(response);
          },(error) => {
            console.log(error);
            this.btnLoader= false;
            this.fileUploaderSnackText= 'خطا در حذف فایل. لطفا دوباره تلاش کنید'
            this.fileUploaderSnackBarAlertColor= 'red';
            this.fileUploaderSnackBarAlert= true;
            this.deleteDocumentDialog= false;
          });
          /**
           *call fetchData from Parent and update all records in background.
           *
           *
           */
          this.$emit('fetchData');
        }
      },

      getBinaryFile(attachment) {
        //console.log(JSON.stringify(attachment));
        let fileUrl = '/file/' + attachment.file.url;
        //const response = await this.$axios.$get(fileUrl);
        //let file = await response;
        window.open(process.env.apiBaseUrl +fileUrl );
      },

      destroyElement(){
        this.documentAttachmentAPI = [];
        this._documentAttachment = [];
        this.registryDocFile= [];
        this.tempAttachment = [];
      },

    },
  };
</script>
