# OverView
&nbsp;

&nbsp; Complete and easy file uploader with image compressor in Vue.js


+ Choice Theme : Thumbnail, simple, Table
+ Image compressor
+ Select level for Image compressor
+ Select file extension
+ Manage files count
+ Manage files size
+ Multi language support
+ Right to left support
+ ...

&nbsp;

# Install


``` bash
$npm install vue-file-uploader
```

&nbsp;

## Build Setup

&nbsp;

&nbsp;&nbsp;&nbsp;Import vue-file-uploader to project

``` js
import vueFileUploader from 'vue-file-uploader'
```


# props
&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; `documentAttachment`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The documentAttachment return array of uploaded file

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Array `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :setDocumentAttachment="setInsertedFile"
    v-model:documentAttachment="registryDocFile"
  >
 <vue-file-uploader>
 ```

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  method:
``` js
 methods:{
     setInsertedFile(item){
       this.registryDocFile = item;
     },
  }
 ```
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return Array:

``` js
[
    { 
        file: {
            base64: 'base64', 
            size: 'file size',
            name: 'file name',
            format 'file upload format. for example:image/jpeg;base64'
        }
    }
 ]
```
---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `fileUploaderType`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The fileUploaderType define file uploader theme : `thumbnaile`  , `simple` ,  `table`

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` String `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` thumbnail ` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :fileUploaderType= "thumbnail"
  >
 <vue-file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <vue-file-uploader
    :fileUploaderType= "simple"
  >
 <vue-file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <vue-file-uploader
    :fileUploaderType= "table"
  >
 <vue-file-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `cardType`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Choose File Uploader Card Type Theme
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cardTypes : &nbsp;  &nbsp;`default` &nbsp;, &nbsp; &nbsp; `outlined`&nbsp;, &nbsp; &nbsp;`shaped`&nbsp;, &nbsp;&nbsp; `raised`&nbsp;, &nbsp; &nbsp;`tile`

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` String `
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` default `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :cardType= "'shaped'"
  >
 <vue-file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding.


---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `fileAccept`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The fileAccept attribute of the input tag, MIME type

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` String `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :fileAccept= "'image/png,image/gif,image/jpeg,image/webp'"
  >
 <vue-file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Important: ` If don`t send fileAccept, file uploader accept all file formats.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding.



---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `imageCompressor`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; vue file uploader, Uses the Browser's native [canvas.toBlob](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/toBlob) API to do the compression work, which means it is lossy compression. General use this to precompress a client image file before upload it.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` true ` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :imageCompressor= "true"
 <vue-file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <vue-file-uploader
   :imageCompressor.sync= "true"
  >
 <vue-file-uploader>
 ```


---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `imageCompressLevel`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; A Number between 0 and 1 indicating image quality.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Number `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` 0.5 ` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :imageCompressLevel= "0.6"
  >
 <vue-file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding.

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `maxFileSize`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Maximum of file size upload. sent in prop to KB

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Number `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` 5120 `  &nbsp;kb

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :maxFileSize= "1024"
  >
 <vue-file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. get more: [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <vue-file-uploader
    :maxFileSize.sync= "10240"
  >
 <vue-file-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `maxFileCount`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Maximum of file upload

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Number `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` 0 ` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :maxFileSize= "5"
  >
 <vue-file-uploader>
 ```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If you dont send maxFileCount, You can upload files without restrictions.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. get more: [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <vue-file-uploader
    :maxFileSize.sync= "10"
  >
 <vue-file-uploader
 ```
---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `thumb`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; show / hidden thumb for images in `table` and `simple` file uploader

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `true` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :thumb= "true"
  >
 <vue-file-uploader>
 ```
---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `tableThumbColumn`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; show / hidden thumb column in `table` file uploader

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `true` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :tableThumbColumn= "true"
  >
 <vue-file-uploader>
 ```
---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `tableFixedHeader`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; enable / disable table fixed header

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `true` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :tableFixedHeader= "true"
  >
 <vue-file-uploader>
 ```
---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `tableHeight`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set table height in `px`.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Number `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `400` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :tableHeight= "500"
  >
 <vue-file-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `badgeCounter`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Badge file counter state.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `true` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :badgeCounter= "false"
  >
 <vue-file-uploader>
 ```
---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `rtlSupport`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Enable RTL support languages.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `false` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :rtlSupport= "true"
  >
 <vue-file-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `lang`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Change file uploader languages.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Examples: &nbsp; English  &nbsp;`en` &nbsp;, &nbsp; Persian &nbsp; `fa`&nbsp;, &nbsp; French &nbsp;`fr`&nbsp;, &nbsp;Chinese &nbsp; `ch`&nbsp;, &nbsp; Arabic &nbsp;`ar`

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` String `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `en` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :lang= "fa"
  >
 <vue-file-uploader>
 ```
---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `btnColor`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; change Button color.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` String `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `info` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <vue-file-uploader
    :btnColor= "'#00796B'"
  >
 <vue-file-uploader>
 ```

---
&nbsp;

# Refs
&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; destroyFileUploader()

&nbsp;

 &nbsp;&nbsp;&nbsp;&nbsp; With this method you can destroy file uploader component.
 
 ``` html
 <vue-file-uploader
     :setDocumentAttachment="setInsertedFile"
     v-model:documentAttachment="registryDocFile"
     :fileUploaderType= "'thumbnail'"
     :maxFileSize= "10240"
     :imageCompressor= "true"
     :imageCompressLevel= "0.8"
     :maxFileCount="10"
     :cardType= "default"
     :badgeCounter= "true"
     :rtlSupport= "true"
     :lang= "'fr'"
     ref="fileUploader"
 >
 </vue-file-uploader>
 ```
&nbsp;&nbsp;&nbsp;&nbsp; Use `ref` in component. similar to above example. then call this method 
``` js
 this.refs.fileUploader.destroyFileUploader();
```

---
&nbsp;

# Code Examples
&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; Thumbnail

``` html
<vue-file-uploader
    :setDocumentAttachment="setInsertedFile"
    v-model:documentAttachment="registryDocFile"
    :fileUploaderType= "'thumbnail'"
    :maxFileSize= "10240"
    :imageCompressor= "true"
    :imageCompressLevel= "0.8"
    :maxFileCount="10"
    :cardType= "default"
    :badgeCounter= "true"
    :rtlSupport= "true"
    :lang= "'fr'"
    ref="fileUploader"
>
</vue-file-uploader>
```

``` js
<script>
    import vueFileUploader from 'vue-file-uploader';
    export default {
        components: {
            vueFileUploader,
        },
        data: () => ({
            registryDocFile: [],
        }),
        methods:{
            setInsertedFile(item){
             this.registryDocFile = item;
        },
    }
 </script>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; `registryDocFile` The Array you define for file uploader

&nbsp;

---

&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; Simple

``` html
<vue-file-uploader
    :setDocumentAttachment="setInsertedFile"
    v-model:documentAttachment="registryDocFile"
    :fileUploaderType= "'simple'"
    :maxFileSize= "10240"
    :imageCompressor= "true"
    :imageCompressLevel= "0.8"
    :maxFileCount= "10"
    :cardType= "default"
    :badgeCounter= "true"
    :thumb= "false"
    :rtlSupport= "true"
    :lang= "'fr'"
    ref= "fileUploader"
>
</vue-file-uploader>
```

``` js
<script>
    import vueFileUploader from 'vue-file-uploader';
    export default {
        components: {
            vueFileUploader,
        },
        data: () => ({
            registryDocFile: [],
        }),
        methods:{
            setInsertedFile(item){
             this.registryDocFile = item;
        },
    }
 </script>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; `registryDocFile` The Array you define for file uploader

&nbsp;

---

&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; Table

``` html
<vue-file-uploader
    :setDocumentAttachment="setInsertedFile"
    v-model:documentAttachment="registryDocFile"
    :fileUploaderType= "'table'"
    :maxFileSize= "10240"
    :imageCompressor= "true"
    :imageCompressLevel= "0.8"
    :maxFileCount= "10"
    :badgeCounter= "true"
    :thumb= "true"
    :tableFixedHeader= "true"
    :tableHeight= "400"
    :tableThumbColumn= "true"
    :lang.sync= "'fr'"
    :rtlSupport= "true"
    ref="fileUploader"
>
</vue-file-uploader>
```

``` js
<script>
    import vueFileUploader from 'vue-file-uploader';
    export default {
        components: {
            vueFileUploader,
        },
        data: () => ({
            registryDocFile: [],
        }),
        methods:{
            setInsertedFile(item){
             this.registryDocFile = item;
        },
    }
 </script>
```

&nbsp;&nbsp;&nbsp;&nbsp; `registryDocFile` The Array you define for file uploader
