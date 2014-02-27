User styles, just like regular stylesheets, select specific elements using [CSS selectors](http://www.w3.org/TR/selectors/).

When writing HTML, you can modify the markup to more easily apply CSS by including IDs and classes. When writing user styles, you of course cannot control the HTML markup. This means that sometimes you need to get creative to match the elements you want. There are a few strategies you can use:

* Use [combinators](http://www.w3.org/TR/selectors/#combinators) to start from an element that does have an ID or class.
* [Attribute selectors](http://www.w3.org/TR/selectors/#attribute-selectors) work well if the element has a unique combination of attributes.
* [Structural pseudo-classes](http://www.w3.org/TR/selectors/#structural-pseudos) select elements based on their position in the document.

For example, given this markup:
```html
<table id="prices">
	<tbody>
		<tr>
			<td>Hamburger</td>
			<td>$5.00</td>
		</tr>
		<tr>
			<td>Hot dog</td>
			<td>$4.00</td>
		</tr>
		<tr>
			<td>Taco</td>
			<td>$5.25</td>
		</tr>
	</tbody>
</table>
```
If you wanted to right-align the second column, you could use this selector:

```css
#prices td:nth-child(2)
```

Given this markup:
```html
<div class="container">
	<p>Paragraph one</p>
	<p>Paragraph two</p>
	<p>Maybe the number of paragraphs changes per page.</p>
	<p style="float: right">A floating aside on the page.</p>
	<p>More paragraphs...</p>
</div>
```

If we wanted to hide the floating aside, a type selector with a combinator (e.g. .container p) would not work because it's the same element as the other content, and a structural pseudo-class would not work because the number of paragraphs (and thus the aside's position) is variable. Instead, we can use an attribute selector:

```css
.container p[style="float: right"] {
	display: none !important;
}
```

### Tools

In Firefox, Stylish installs a selector tool to [DOM Inspector](https://addons.mozilla.org/en-US/firefox/addon/dom-inspector-6622/). Right clicking a node in the left side view provides a Copy Selector menu with suggestions of selectors to use.

Another tool for automatically generating selectors is the [Selector Gadget](http://selectorgadget.com/) bookmarklet. If you click on the elements you want to select and then on elements you want to exclude it will try to generate the simplest selectors for that.