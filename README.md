# data-imgsrc
### Conditional loading of images, with source URLs referenced in HTML

## Usage

**data-imgsrc** looks for the presence of the `data-imgsrc` attribute on either placeholder elements or links.

### Using with a placeholder elements
You can add the `data-imgsrc` attribute to a placeholder element (such as `<div>`).

```html
<div class="pull-left" data-imgsrc="/path/to/image.jpg">Fallback content</div>
```

This element will be swapped for an image when the script runs and the conditions for loading images are met:

```html
<img class="pull-left" src="/path/to/image.jpg"/>
```

Any classes added to this placeholder will be carried over to the image as well.

### Using on a link to high resolution image
If your markup contains thumbnails that linking to larger resolution images (say for example, in a slideshow), you can use the `data-imgsrc` attribute without providing any value; instead it will look to the contents of the `href` attribute instead. For example, the following:

```html
<a href="/path/to/image_hires.jpg" title="View a larger version of this photo (116kb)"><img src="/path/to/image_lowres.jpg" width="360" alt=""/></a>
```

Will be replaced like so:

```html
<img class="pull-left" src="/path/to/image_hires.jpg"/>
```

### the `loadImgs` function
Once you have attached the `data-imgsrc` attribute to the placeholder elements and links you wish to enhance, you can then call the `loadImgs()` function at the end of your document:

```html
<script src="data-imgsrc.js"></script>
<script>
	loadImgs();
</script>
```

Of course, this script becomes more useful when combined with testing for certain conditions. For example, if wanted to only show (larger) images when the viewport was wider than 640px, you could do the following:

```html
<script src="data-imgsrc.js"></script>
<script>
	if (window.matchMedia && window.matchMedia("(min-width: 40em)").matches) {
		loadImgs();
	}
<script>
```

Alternatively, we might wish to only load image enhancements above certain bandwidth criteria (i.e. for agents that support the [Network Information API](http://www.w3.org/TR/netinfo-api/)):

```html
<script src="data-imgsrc.js"></script>
<script>
	if (navigator.connection && navigator.connection.bandwidth >= 750) {
		 loadImgs();
	}
<script>
```

## Credits
Concept: Paul Robert Lloyd (<http://paulrobertlloyd.com/>)
Initial code: Josh Emerson (<http://joshemerson.co.uk/>)

## License
This work is available under the MIT license: <http://paulrobertlloyd.mit-license.org/>