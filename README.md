# ngx-simple-image-upload

An Angular Component for upload images and read them inline.

This version work with **Angular 2+** versions, if you are looking for Angular 1.x and jQuery please visit [simpleImageUpload](https://github.com/elporfirio/simpleImageUpload) repository.

![angular logo](https://github.com/elporfirio/ngx-simple-image-upload/raw/master/docs/siu-logo.png)

## Requirements:

* jQuery 1.11+
* Angular 2+ (currently tested on Angular 5)

### Browser Support:

Desktop

| IE    | Chrome  | Firefox | Safari |
| :----: | :------: | :------:| :----: |
| 11    | 63+     | 57+     |  11    |

Mobile

| iOS Safari | Chrome   | UC Android |
| :----:     | :------: | :------:   |
| 10.2       | 62       | 11.4       |

## Installation

Install via npm

`npm i ngx-simple-image-upload`

or [download via GitHub](https://github.com/elporfirio/simpleImageUpload/archive/master.zip)


## Usage

Feel free to change styles located in <span style='color:blue'>simple-image-upload.component.css</span> according to your project.

Add jQuery to angular-cli.json (if you install via npm)

```
...

  "scripts": [
    "../node_modules/jquery/dist/jquery.js"
  ],

...
```

Import *SimpleImageUploadModule* into your module.

`import { SimpleImageUploadModule } from 'ngx-simple-image-upload';`


Add Module to your inputs:

```
  declarations: [
    ...
  ],
  imports: [
    ...
    SimpleImageUploadModule
    ...
  ],
  providers: [],
  bootstrap: [AppComponent],
```

Until Fixed and properly compiled add

`../node_modules/ngx-simple-image-upload/index.ts`

To tsconfig.json

Then use the componente as follow:

`<simple-image-upload (onFileReaded)="doSome($event)"></simple-image-upload>`

### Callbacks


| Name    | Return Type   | Description   |
| ----------- | ----------- | ----------- |
| onFileReaded | imageFile | Returns imageFile object after process image |

### imageFile Type

```
{
    "source": "data:image;base64",
    "file": {File Object},
    "name": "imageName.jpg"
}
```

### Fix Issue with Angular4/5

For error *node_modules/ngx-simple-image-upload/index.ts is missing from the TypeScript compilation.*

Add the "include" node into `tsconfig.app.json` (where *app* is your main module)

```
  "include": [
    "../src/**/*",
    "../node_modules/ngx-simple-image-upload/index.ts"
    ...
  ],
```


## Example

Declare method in your main module, this method will receive the `imageFile`.

```
  setImage(imageFile){
    this.image = imageFile.source;
  }
```

Use source like src attribute:


```<img src="{{ this.image }}>```


And add the method to callback:

```<simple-image-upload (onFileReaded)="setImage($event)"></simple-image-upload>```



## Demo

See demo on [https://elporfirio.github.io/simpleImageUpload/](https://elporfirio.github.io/simpleImageUpload/).

# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [1.0.0] - 2018-01-15
### Initial Release
- Nothing Special to report


[Unreleased]: https://github.com/elporfirio/simpleImageUpload
[1.0.0]: https://github.com/elporfirio/ngx-simple-image-upload/releases/tag/v1.0.0

[simple-image-upload-logo.png]: data:image/png;base64,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
