# data-imgsrc.js
### Conditional loading of images, with source URLs referenced in HTML

## Usage

**data-imgsrc** looks for the presence of a `data-imgsrc` attribute on either placeholder elements or links to higher resolution images.

### Using with placeholder elements
You can add the `data-imgsrc` attribute to a placeholder element (such as `<div>`).

```html
<div class="pull-left" data-imgsrc="/path/to/image.jpg">Fallback content</div>
```

This element will be swapped out for an image when the script runs and the conditions for loading images are met:

```html
<img class="pull-left" src="/path/to/image.jpg"/>
```

Any classes added to this placeholder will be carried over to the image as well.

### Using on links to high resolution image
If your markup contains thumbnails linking to larger resolution images (say for example in a slideshow), you can use a valueless `data-imgsrc` attribute, and the value of the `href` attribute will be used instead. For example, the following linked thhumbnail image:

```html
<a class="pull-left" data-imgsrc href="/path/to/image_hires.jpg" title="View a larger version of this photo (116kb)"><img src="/path/to/image_lowres.jpg" width="360" alt=""/></a>
```

Will be replaced like so:

```html
<img class="pull-left"  class="pull-left" src="/path/to/image_hires.jpg"/>
```

Again, any classes added to this link will be carried over to new image.

### the `loadImgs` function
Once you have added the `data-imgsrc` attribute to placeholder elements and any links you wish to enhance, you can then call the `loadImgs()` function at the end of your document:

```html
<script src="data-imgsrc.js"></script>
<script>
	loadImgs();
</script>
```

Of course, this script becomes much more useful when combined with testing for certain conditions. For example, if wanted to only show enhanced images when the viewport is wider than 640px, you could use the following:

```html
<script src="data-imgsrc.js"></script>
<script>
	if (window.matchMedia && window.matchMedia("(min-width: 40em)").matches) {
		loadImgs();
	}
<script>
```

Alternatively, you might wish to load your image enhancements above a certain bandwidth criteria (i.e. for agents that support the [Network Information API](http://www.w3.org/TR/netinfo-api/)):

```html
<script src="data-imgsrc.js"></script>
<script>
	if (navigator.connection && navigator.connection.bandwidth >= 750) {
		 loadImgs();
	}
<script>
```
## Examples
Examples of this script being used to enhance common design patterns can be found here: <http://paulrobertlloyd.github.com/responsivepatterns/>

## Credits
Concept: Paul Robert Lloyd (<http://paulrobertlloyd.com/>)
Initial code: Josh Emerson (<http://joshemerson.co.uk/>)

## License
This work is available under the MIT license: <http://paulrobertlloyd.mit-license.org/>