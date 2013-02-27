# data-imgsrc.js
### Conditional loading of images, with image paths specified in HTML

* Lightweight
* No dependencies
* Requires support for the [Selectors API](http://www.w3.org/TR/selectors-api/) (but could easily be rewritten not to)

## Usage

### Using a placeholder element
Add the `data-imgsrc` attribute to a placeholder element (such as `<div>`). It's value should contain a URL to the image you wish to conditionally load. Classes added to this placeholder will be carried over to the image. For example:

```html
<div class="pull-left" data-imgsrc="/path/to/image.jpg">Fallback content</div>
```

Should the conditions for enhanced images be met, this element will be replaced with an image, as follows:

```html
<img class="pull-left" src="/path/to/image.jpg"/>
```

### Using linked thumbnail images
If your markup contains thumbnails that link through to higher resolution images (say within a photo gallery or carousel that is progressively enhanced), you can simply add a valueless `data-imgsrc` attribute to each link. The value of the `href` attribute will be utilised by this script. For example, the following linked thumbnail:

```html
<a class="pull-left" data-imgsrc href="/path/to/image_hires.jpg" title="View a larger version of this photo (116kb)"><img src="/path/to/image_lowres.jpg" width="360" alt=""/></a>
```

will be replaced as follows:

```html
<img class="pull-left"  class="pull-left" src="/path/to/image_hires.jpg"/>
```

Again, any classes added to this link will be carried over to new image.

### The `loadImgs` function
Once you have added the `data-imgsrc` attribute to placeholder elements and any linked thumbnails, call the `loadImgs()` function at the end of your document:

```html
<script src="data-imgsrc.js"></script>
<script>
	loadImgs();
</script>
```

Of course, this script is much more useful when combined with testing for certain device properties. For example, if you wanted to load enhanced images only when the viewport is wider than 640px, you could do so as follows:

```html
<script src="data-imgsrc.js"></script>
<script>
	if (window.matchMedia && window.matchMedia("(min-width: 40em)").matches) {
		loadImgs();
	}
<script>
```

Alternatively, you might wish to load image enhancements above certain bandwidth criteria (i.e. for agents that support the [Network Information API](http://www.w3.org/TR/netinfo-api/)):

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
This work is made available under the MIT license: <http://paulrobertlloyd.mit-license.org/>