# OverView
&nbsp;

&nbsp; Complete and simple file uploader with image compressor in Vue.js


+ Choice Theme : Thumbnail, Simple, Table
+ Add custom fields (Title, Description, Tags, ...)
+ Image compressor
+ Select level for Image compressor
+ Mange file extensions
+ Manage files count
+ Manage files size
+ Multi language support
+ Right to left support
+ ...
&nbsp;

&nbsp;
# Install

&nbsp;

&nbsp;&nbsp;&nbsp;1. Install package:
``` bash
$npm install handy-uploader
```


&nbsp;&nbsp;&nbsp;2. You should Install Vuetify on project:

### &nbsp;&nbsp;  Install on Vue CLI
``` bash
$vue add vuetify
```
### &nbsp;&nbsp;  Install on Nuxt
``` bash
$npm install @nuxtjs/vuetify -D
```
&nbsp;&nbsp;&nbsp;Once installed, update your `nuxt.config.js` file to include the Vuetify module in the build.

``` js
// nuxt.config.js
{
  buildModules: [
    '@nuxtjs/vuetify',
}
```


## Build Setup

&nbsp;

&nbsp;&nbsp;&nbsp;Import handy-uploader to project

``` js
<script>
    import handyUploader from 'handy-uploader/src/components/handyUploader';
    export default {
        components: {
            handyUploader,
        },
    }
 </script>
```

&nbsp;

### &nbsp;&nbsp;&nbsp;Import handy-uploader to project - Full Example

``` html
<handy-uploader
    :documentAttachment.sync="handyAttachments"
    :fileUploaderType= "'simple'"
    :maxFileSize= "10240"
    :imageCompressor= "true"
    :imageCompressLevel= "0.8"
    :maxFileCount= "10"
    :badgeCounter= "true"
    :thumb= "false"
    :changeFileName="true"
    :addFileDescription="true"
    :addFileTag="true"
    :tags= "['Tag 1', 'Tag 2', 'Tag 3', 'Tag 4']"
>
</handy-uploader>
```

``` js
<script>
    import handyUploader from 'handy-uploader/src/components/handyUploader';
    export default {
        components: {
            handyUploader,
        },
        data: () => ({
            handyAttachments: [],
        }),
    }
 </script>
```
---

&nbsp;

# props
&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; `documentAttachment`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The documentAttachment return array of uploaded file

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Array `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <handy-uploader
    :documentAttachment.sync="handyAttachments"
  >
 <handy-uploader>
 ```

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return Array:

``` js
[
    { 
        file: {
            base64: 'base64', 
            size: 'file size',
            name: 'file name',
            format: 'file upload format. for example:image/jpeg;base64'
            tags: [],
            description: 'file description'
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
 <handy-uploader
    :fileUploaderType= "thumbnail"
  >
 <handy-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <handy-uploader
    :fileUploaderType= "simple"
  >
 <handy-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; or

``` html
 <handy-uploader
    :fileUploaderType= "table"
  >
 <handy-uploader>
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
 <handy-uploader
    :cardType= "'shaped'"
  >
 <handy-uploader>
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
 <handy-uploader
    :fileAccept= "'image/png,image/gif,image/jpeg,image/webp'"
  >
 <handy-uploader>
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
 <handy-uploader
    :imageCompressor= "true"
 <handy-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <handy-uploader
   :imageCompressor.sync= "true"
  >
 <handy-uploader>
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
 <handy-uploader
    :imageCompressLevel= "0.6"
  >
 <handy-uploader>
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
 <handy-uploader
    :maxFileSize= "10240"
  >
 <handy-uploader>
 ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. get more: [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <handy-uploader
    :maxFileSize.sync= "10240"
  >
 <handy-uploader>
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
 <handy-uploader
    :maxFileSize= "5"
  >
 <handy-uploader>
 ```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If you dont send maxFileCount, You can upload files without restrictions.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; you can use `sync` to enable tow-way-binding. get more: [.sync Modifier](https://vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)
``` html
 <handy-uploader
    :maxFileSize.sync= "10"
  >
 <handy-uploader
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
 <handy-uploader
    :thumb= "true"
  >
 <handy-uploader>
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
 <handy-uploader
    :tableThumbColumn= "false"
  >
 <handy-uploader>
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
 <handy-uploader
    :tableFixedHeader= "false"
  >
 <handy-uploader>
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
 <handy-uploader
    :tableHeight= "500"
  >
 <handy-uploader>
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
 <handy-uploader
    :badgeCounter= "false"
  >
 <handy-uploader>
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
 <handy-uploader
    :rtlSupport= "true"
  >
 <handy-uploader>
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
 <handy-uploader
    :lang= "'fa'"
  >
 <handy-uploader>
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
 <handy-uploader
    :btnColor= "'#00796B'"
  >
 <handy-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `changeFileName`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Change file name before upload.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `false` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <handy-uploader
    :changeFileName= "true"
  >
 <handy-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `addFileDescription`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Add file Description before upload.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `false` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <handy-uploader
    :addFileDescription= "true"
  >
 <handy-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `addFileTag`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Add file tags before upload.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Boolean `

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; `false` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <handy-uploader
    :addFileTag= "true"
  >
 <handy-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `tags`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Array of file tags.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Array ` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <handy-uploader
    :tags= "['Tag 1', 'Tag 2', 'Tag 3', 'Tag 4']"
  >
 <handy-uploader>
 ```

---
&nbsp;

### &nbsp;&nbsp;&nbsp;&nbsp; `cols`
&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Change count of columns.

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Type: &nbsp;&nbsp; ` Number ` 
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Default: &nbsp;&nbsp; ` 4 ` 

#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  Usage:
``` html
 <handy-uploader
    :cols= "6"
  >
 <handy-uploader>
 ```

---
&nbsp;



# Code Examples
&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; Thumbnail

``` html
<handy-uploader
    :documentAttachment.sync="handyAttachments"
    :fileUploaderType= "'thumbnail'"
    :maxFileSize= "10240"
    :imageCompressor= "true"
    :imageCompressLevel= "0.8"
    :maxFileCount="10"
    :badgeCounter= "true"
    :changeFileName="true"
    :addFileDescription="true"
    :addFileTag="true"
    :tags= "['Tag 1', 'Tag 2', 'Tag 3', 'Tag 4']"
>
</vue-file-uploader>
```

``` js
<script>
    import handyUploader from 'handy-uploader/src/components/handyUploader';
    export default {
        components: {
            handyUploader,
        },
        data: () => ({
            handyAttachments: [],
        }),
    }
 </script>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; `handyAttachments` The Array you define for file uploader

&nbsp;

---

&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; Simple

``` html
<vue-file-uploader
    :documentAttachment.sync="handyAttachments"
    :fileUploaderType= "'simple'"
    :maxFileSize= "10240"
    :imageCompressor= "true"
    :imageCompressLevel= "0.8"
    :maxFileCount= "10"
    :badgeCounter= "true"
    :thumb= "false"
    :changeFileName="true"
    :addFileDescription="true"
    :addFileTag="true"
    :tags= "['Tag 1', 'Tag 2', 'Tag 3', 'Tag 4']"
>
</handy-uploader>
```

``` js
<script>
    import handyUploader from 'handy-uploader/src/components/handyUploader';
    export default {
        components: {
            handyUploader,
        },
        data: () => ({
            handyAttachments: [],
        }),
    }
 </script>
 ```

&nbsp;&nbsp;&nbsp;&nbsp; `handyAttachments` The Array you define for file uploader

&nbsp;

---

&nbsp;
### &nbsp;&nbsp;&nbsp;&nbsp; Table

``` html
<handy-uploader
    :documentAttachment.sync="handyAttachments"
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
    :changeFileName="true"
    :addFileDescription="true"
    :addFileTag="true"
    :tags= "['Tag 1', 'Tag 2', 'Tag 3', 'Tag 4']"
>
</handy-uploader>
```

``` js
<script>
    import handyUploader from 'handy-uploader/src/components/handyUploader';
    export default {
        components: {
            handyUploader,
        },
        data: () => ({
            handyAttachments: [],
        }),
    }
 </script>
```

&nbsp;&nbsp;&nbsp;&nbsp; `handyAttachments` The Array you define for file uploader
