Styles posted on userstyles.org are automatically categorized based on the code they contain. The main checks are for @-moz-document rules and default namespaces.

@-moz-document rules specify which URLs a section of code applies to. See [Applying styles to specific sites](Applying styles to specific sites) for more information.

[CSS namespaces](http://www.w3.org/TR/css3-namespace/) are a standard CSS feature that help to remove ambiguity between XML tags with the same tag name but under the same namespace. In reality, declaring CSS namespaces is rarely needed, but is helpful to include to better inform userstyles.org of what kind of style you've written. The most commonly used namespace would be to set XUL as the default namespace. Adding this to the top of the style would do so:

```css
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
```

The rules userstyles.org uses for determining a category are as follows:

1. If XUL is the default namespace, the style is an "app" style.
2. If there are no @-moz-document rules, the style is a "global" style.
3. If any of the @-moz-document rules are for the chrome, about, or x-jsd protocols, the style is an "app" style.
4. If any of the @-moz-document rules are of "url-prefix" type and apply to the entirety of the http, https, ftp, file, data, or chm:file protocols, the style is a "global" style.
5. Otherwise, the style is a "site" style.

To calculate the subcategory:

* If the category is "site", the first @-moz-document rule's value has is stripped (e.g. "www.example.com" becomes "example") and this is the subcategory. IP addresses are skipped if non-IP address values are present.
* If the category is "app", the URL is checked against a map of common URL prefixes and the resulting value is the subcategory. If the URL does not match any common prefixes, the subcategory is "browser".
* Global styles do not have a subcategory.