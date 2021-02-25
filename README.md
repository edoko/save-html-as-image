# save-html-as-image

[![npm version](https://badge.fury.io/js/save-html-as-image.svg)](https://badge.fury.io/js/save-html-as-image)


This can be used for a couple of things, it can save HTML (DOM) as an image (JPG,PNG) and it can convert SVG images to PNG.
Convering SVG to PNG is useful for Safari Browser compatibility since it cannot render SVG images.

## Usage

```js
import { saveAsPng, saveAsJpeg } from 'save-html-as-image';

const node = document.getElementById('elementId');

//download the node as png. Image (2019-12-01).png
saveAsPng(node);

//download the node as png. Report (2019-12-01).png
saveAsPng(node, {  filename: 'Report', printDate: true });

//download the node as jpeg. Album.jpeg
saveAsJpeg(node, {  filename: 'Album', printDate: false });

```

## Options

The options are: 
- **filename** : The name of the file when download.
- **printDate** : The date of the download.
- **forceFixText** : Prevent some error with text.


## Hide Elements

You can hide elements adding the class **"hide-when-downloading"**.

Hide elements apply `display: hidden` to the elements with this class;

```
  <section>
    <article>One..</article>
    <article class="hide-when-downloading">Two...</article>
  </section>
```

```
saveAsPng(node, {  filename: 'News', printDate: true });
  //Only the first article will be visible on the image
```

**Note**: The class "hide-when-downloading" must be on root element, That we want hide.

## Remove Elements

You can remove elements adding the class **"remove-when-downloading"**.

Remove Elements apply `display: none` to the elements. So the space into the element will remove.


## Browsers
It's tested on the lasted Chrome (Chrome 76),  Firefox and *Safari*.

We resolve the Safari support with a litte hack and replace svg with image. It's tested with FontAwesomeIcons svgs.


## Dependency

We use a collection of packages to generate and donwnload images, all in one action.
The packages are:

- 'file-saver'
- 'html-to-image'
- 'save-svg-as-png'

## How it work

- This library use **html-to-image** library for convert the HTML (DOM) to Image (jpg and png).
- We use file saver to download the image generated.
- We use save-svg-as-png to convert the svgs to img elements, only on safary or browser with stricter secure on **<foreignObject>**
