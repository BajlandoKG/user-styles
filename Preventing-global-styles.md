Global styles are styles that will be applied to all sites the user visits. Some style authors will accidentally post global styles to userstyles.org when they intend to post styles that are more specific. This page will describe how to prevent this from occurring.

## Authoring in Chrome or Opera

If you create your style in Chrome or Opera, you can use the "Applies to" controls to limit what site your style is active on. To retain this information when posting to userstyles.org, click the "To Mozilla format" button and use the resulting code as your CSS. Chrome and Opera users will have this code translated back into the appropriate format when they install your style.


## Authoring in Firefox

If you create your style in Firefox, you can use @-moz-document rules to specify to limit what site your style is active on. For example, to make your code apply only to pages on the domain "example.com", you would use the following code:

```css
@-moz-document domain(example.com) {
	/* your code goes here */
}
```

Ensure your code is followed by the closing bracket for the @-moz-document block, as shown above.

For more detailed usage of @-moz-document rules, see [Applying styles to specific sites](https://github.com/JasonBarnabe/stylish/wiki/Applying-styles-to-specific-sites).


## Firefox app styles

Firefox users have the ability to have styles that apply to Firefox's own user interface: toolbars, dialogs, tabs, etc. If you intend to have your style do this, include this line at the top of your code:

```css
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
```

This says that the default namespace of your style is XUL. XUL is the language Firefox's user interface is written in; defining it as the default makes your style specific to XUL and lets userstyles.org understand what you intend.


## If you really want a global style...

The intent of this page is to prevent accidentally posting non-global code as global styles. Global styles are allowed on userstyles.org. If you understand that your style will be applied to all sites, and that's what you intend, include the following code anywhere in your style:

```css
/* i really want this to be global */
```