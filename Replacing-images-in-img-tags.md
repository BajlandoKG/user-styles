While replacing background images is easy with CSS, replacing images created with <img> tags is not. You need to do the following trick to switch <img> tag images.

```css
#your-selector-here {
	height: 0 !important;
	width: 0 !important;
	/* these numbers match the new image's dimensions */
	padding-left: 125px !important;
	padding-top: 25px !important;
	background: url(http://example.com/your/image/here) no-repeat !important;
}
```