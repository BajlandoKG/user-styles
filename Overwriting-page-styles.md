An important consideration when writing user styles is that you need your style rules to override any existing rules for the same elements. Which rule wins when two apply to the same property of the same element is determined by [CSS cascade rules](http://www.w3.org/TR/2011/REC-CSS2-20110607/cascade.html#cascading-order).

## Origin

Due to technological differences, your styles may be applied at different points in the cascade depending on the method users use to install it.

* Stylish for Firefox and other Mozilla programs: the last author sheet (this can be changed, see AGENT_SHEET below)
* Greasemonkey: the first author sheet
* Stylish for Chrome, if the style installed while a page it affects is open: last author sheet. On subsequent page loads: first author sheet.
* Tampermonkey: the first author sheet

## Recommendations

It's recommended that all your declarations include the `!important` keyword. This will give your rules the best chance of applying without additional changes. An example of `!important`:

```css
a {
	text-decoration: none !important;
}
```

When two rules have the same !importance, the one with the highest [specificity](http://www.w3.org/TR/2011/REC-CSS2-20110607/cascade.html#specificity) wins. You can artificially increase your specificity by writing longer selectors. For example, given the markup:

```html
<div id="foo">
	<span id="bar">text</span>
</div>
```

and the site specifies:
```css
#bar {
	color: red !important;
}
```

you can ensure that you win by using a more specific selector, like `#foo #bar`, `div #bar`, `span#bar`, etc.

In the event of equal specificity, the latest defined (furthest down the page) stylesheet wins. Per the previous section, this means you may or may not win, depending on the browser used. You should avoid this situation by increasing your selectors' specificity.

## AGENT_SHEET

With Stylish for Firefox, you can include

```css
/* AGENT_SHEET */
```

anywhere in your style to make it be applied as an agent sheet. This is intended to allow your style to override Firefox internals like scrollbars for app style and form elements like checkbox and radio button for site style which are only possible in agent sheet mode.

**This comment only has an effect in Stylish for Firefox. You can cause Firefox to crash with agent sheets. Therefore, it's recommended to only use this mode when you need it.**