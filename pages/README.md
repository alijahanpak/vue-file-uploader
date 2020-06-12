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

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` file `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <file-uploader
    :setDocumentAttachment="setInsertedFile"
    v-model:documentAttachment="registryDocFile"
  >
 <file-uploader
 ```
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return Array:

``` js
[{ file:{binary: 'base64', size: 'file size', name: 'file name', format 'file upload format example:image/jpeg;base64'}}]
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
 <file-uploader
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <file-uploader
    :fileUploaderType= "simple"
  >
 <file-uploader
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <file-uploader
    :fileUploaderType= "table"
  >
 <file-uploader
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `imageCompressor`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; vue file uploader, Uses the Browser's native canvas.toBlob API to do the compression work, which means it is lossy compression. General use this to &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; precompress a client image file before upload it.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` true ` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <file-uploader
    :imageCompressor= "true"
 <file-uploader
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding.
``` html
 <file-uploader
   :imageCompressor.sync= "true"
  >
 <file-uploader
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `maxFileSize`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The documentAttachment return array of uploaded file

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Number `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` 5120 `  &nbsp;kb

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <file-uploader
    :maxFileSize= "maxFileSizeChange"
  >
 <file-uploader
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. get more: [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <file-uploader
    :maxFileSize.sync= "maxFileSizeChange"
  >
 <file-uploader
 ```
