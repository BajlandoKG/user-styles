Stylish styles can be made specific to certain URLs with [@-moz-document rules](https://developer.mozilla.org/en/CSS/@document).

## Compatibility

Stylish for Firefox and other Mozilla software supports @-moz-document rules.

The @-moz-document format is the supported format when posting on [userstyles.org](http://userstyles.org). The site software handles converting to other formats for browsers that do not support it.

Stylish on Chrome does not support @-moz-document rules, but provides a UI with the same rule types. It also has a feature to output styles to @-moz-document format, which is useful when you want to post them on userstyles.org.

## Rule types

There are four @-moz-document rule types:
* url - for exact URLs (including the protocol)
* url-prefix - for URLs that start with a certain value (including the protocol)
* domain - for all URLs on a domain (**not** including the protocol)
* regexp - for advanced matching with wildcards (including the protocol)

## Format

@-moz-document rules are specified on the "outside" of normal CSS, just like @media rules. A rule to turn the background of http://www.example.com/test.html black would look like this:

```css
@-moz-document url(http://www.example.com/test.html) {
	body {
		background-color: black !important;
	}
}
```

## Multiple sites

Just like you can create a rule in CSS based on multiple selectors, you can specify multiple values per @-moz-document block. For example:

```css
@-moz-document domain('images.example.com'), url-prefix('http://example.com/images') {
	/* 
		the code in here only applies to:
			-pages on the domain images.example.com
			-pages whose URLs start with http://example.com/images
	*/
}
```

Often, single sites can be accessed on many different URLs and can contain many different kinds of pages. For example, a rule like:

```css
@-moz-document url-prefix("http://www.example.com")
```

would not apply to http://example.com, https://www.example.com or http://www.example.net. You should keep this in mind (and try to account for it!) when writing your @-moz-document rules, especially if you intend on posting your style to userstyles.org for others to use.

## Advanced matching with regular expressions

[Regular expressions](http://www.regular-expressions.info/) offer a powerful way to specify which URLs the style should apply to. Regular expressions are not recommended when the url, url-prefix, and domain rule types will do; they are more difficult to understand and edit, and are more difficult for the userstyles.org software to automatically categorize.

Regular expressions must be escaped using CSS syntax. For example, a . (period) matches any character in regular expressions. To match a literal period, you would first need to escape it using regular expression rules (to \\.), then escape that string using CSS rules (to \\\\.).

The regular expression you write must match the entirety of the URL. This means that using ^ and $ (to match the beginning and end of the string) are unnecessary. Also, using:
```css
@-moz-document regexp('example')
```
would not match http://www.example.com (or anything, for that matter). 

An example of wildcarding in the middle of a URL:
```css
@-moz-document regexp('http://www\\.example\\.(com|de)/images/.*') {
	/* 
		the code in here applies to URLs that start with http://www.example.com/images/
		and http://www.example.de/images/
	*/
}
```

An example of matching all sites with a certain exception:
```css
@-moz-document regexp('(?!http://www\\.example\\.com).*') {
	/*
		the code in here applies to all URLs except those that start with 
		http://www.example.com
	*/
}
```