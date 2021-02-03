# Media Queries

### Media queries don't add any importance or specificity to selectors, so code order matters - media queries at the end.

<br>

For the hover effect but not working on phone or tablet devides, we can use the following method:

```css
@media only screen and (max-width: 56.25rem),
only screen and (hover: none) {
	...
}
```

<img src="img/2.png" width="100%">
<img src="img/1.png" width="100%">

<br><br>


# Responsive Images

### Responsive image in HTML:

For example:

```html
<img srcset="img/nat-1.jpg 300w, img/nat-1-large.jpg 1000w"
	sizes="(max-width: 56.25em) 20vw, (max-width: 37.5em) 30vw, 300px"
	alt="Photo 1"
	class="composition__photo composition__photo--p1"
	src="img/nat-1-large.jpg">

<img srcset="img/nat-2.jpg 300w, img/nat-2-large.jpg 1000w"
	sizes="(max-width: 56.25em) 20vw, (max-width: 37.5em) 30vw, 300px"
	alt="Photo 2"
	class="composition__photo composition__photo--p2"
	src="img/nat-2-large.jpg">

<img srcset="img/nat-3.jpg 300w, img/nat-3-large.jpg 1000w"
	sizes="(max-width: 56.25em) 20vw, (max-width: 37.5em) 30vw, 300px"
	alt="Photo 3"
	class="composition__photo composition__photo--p3"
	src="img/nat-3-large.jpg">
```

another example:

```html
<picture class="footer__logo">
    <source srcset="img/logo-green-small-1x.png 1x, img/logo-green-small-2x.png 2x" media="(max-width: 37.5em)">
    <img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" alt="Full logo" src="img/logo-green-2x.png">
</picture>
```

<br>

### Responsive image in CSS:

Safari doesn't not support `min-resolution`, so we need to use `-webkit-min-device-pixel-ratio` instead.

<img src="img/3.png" width="100%">

```css
/*1.25 dpr*/
@media
only screen and (min-resolution: 120dpi) and (min-width: 37.5rem),
only screen and (-webkit-min-device-pixel-ratio: 1.25) and (min-width: 37.5rem) {
/* When DPR is above 1.25, and min-resolution device resolution is 120dpi, this style will be applied */
}
/*1.5 dpr*/
@media
only screen and (min-resolution: 144dpi) and (min-width: 37.5rem),
only screen and (-webkit-min-device-pixel-ratio: 1.5) and (min-width: 37.5rem) {
/* When DPR is above 1.5, and min-resolution device resolution is 144dpi, this style will be applied */
}

/*2.0 dpr, iPhone use this one*/
@media
only screen and (min-resolution: 192dpi) and (min-width: 37.5rem),
only screen and (-webkit-min-device-pixel-ratio: 2.0) and (min-width: 37.5rem) {
/* When DPR is above 2.0, and min-resolution device resolution is 192dpi, this style will be applied */
}
```

<br>

# Testing for Browser Support with `@supports`

If the browser supports these properties, it will run the inside codes. Otherwise, run the outside codes.

The following codes like `(clip-path: polygon(0 0)) or (-webkit-clip-path: polygon(0 0))`, we can put any values on it, it doesn't matter.

```css
.shape {
	height: 60rem;

	@supports (clip-path: polygon(0 0)) or (-webkit-clip-path: polygon(0 0)) {
		-webkit-clip-path: circle(50% at 50% 50%);
		clip-path: circle(50% at 50% 50%);
		-webkit-shape-outside: circle(50% at 50% 50%);
		shape-outside: circle(50% at 50% 50%);
	}
}
```