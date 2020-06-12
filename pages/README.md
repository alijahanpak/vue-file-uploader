# OverView

&nbsp; vue-file uploader. 


# Install


``` bash
$npm install vue-file-uploader
```


## Build Setup

> Import vue-file-uploader to project

``` js
const VueUploadComponent = require('vue-upload-component')
 Vue.component('file-upload', VueUploadComponent)
```


# props
&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; `documentAttachment`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The documentAttachment return array of uploaded file

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Array `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <file-uploader
    :setDocumentAttachment="setInsertedFile"
    v-model:documentAttachment="registryDocFile"
  >
 <file-uploader>
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
    { file:
        {
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
 <file-uploader
    :fileUploaderType= "thumbnail"
  >
 <file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <file-uploader
    :fileUploaderType= "simple"
  >
 <file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <file-uploader
    :fileUploaderType= "table"
  >
 <file-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `fileAccept`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The fileAccept attribute of the input tag, MIME type

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` String `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <file-uploader
    :fileAccept= "'image/png,image/gif,image/jpeg,image/webp'"
  >
 <file-uploader>
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
 <file-uploader
    :imageCompressor= "true"
 <file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <file-uploader
   :imageCompressor.sync= "true"
  >
 <file-uploader>
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
 <file-uploader
    :imageCompressLevel= "0.6"
 <file-uploader>
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
 <file-uploader
    :maxFileSize= "1024"
  >
 <file-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. get more: [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <file-uploader
    :maxFileSize.sync= "10240"
  >
 <file-uploader>
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
 <file-uploader
    :maxFileSize= "5"
  >
 <file-uploader>
 ```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If you dont send maxFileCount, You can upload files without restrictions.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. get more: [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <file-uploader
    :maxFileSize.sync= "maxFileSizeChange"
  >
 <file-uploader
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
 <file-uploader
    :thumb= "true"
  >
 <file-uploader>
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
 <file-uploader
    :tableThumbColumn= "true"
  >
 <file-uploader>
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
 <file-uploader
    :tableFixedHeader= "true"
  >
 <file-uploader>
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
 <file-uploader
    :tableHeight= "500"
  >
 <file-uploader>
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
 <file-uploader
    :badgeCounter= "false"
  >
 <file-uploader>
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
 <file-uploader
    :rtlSupport= "true"
  >
 <file-uploader>
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
 <file-uploader
    :lang= "fa"
  >
 <file-uploader>
 ```

