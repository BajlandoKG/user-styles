CSS namespaces are used to restrict selectors to elements on a certain XML namespace. For an overview of CSS namespaces, see [@namespace on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@namespace). **A namespace in a user style is not the same as a namespace in a user script. Do not make up your own URL; this can break your style.**

Specifying a CSS namespace in a user style is generally not required as long as the style is [completely specific to a certain site](https://github.com/JasonBarnabe/stylish/wiki/Applying-styles-to-specific-sites). It can be included anyway, if you wish, with the following code at the top of your style:
```css
@namespace url(http://www.w3.org/1999/xhtml);
```
(Do not modify the URL.)

If the user style is supposed to apply globally (i.e. to all web sites), include the same code at the top of your style:
```css
@namespace url(http://www.w3.org/1999/xhtml);
```

If the user style is supposed to apply to Firefox's user interface, include this at the top of your style:
```css
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
```

If you know what you're doing, feel free to use other namespaces or to have multiple ones.