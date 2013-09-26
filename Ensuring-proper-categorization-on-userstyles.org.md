Styles posted on userstyles.org are automatically categorized based on the code they contain. The main factors are the [@-moz-document rules](https://github.com/JasonBarnabe/stylish/wiki/Applying-styles-to-specific-sites), the [@namespace rules](https://github.com/JasonBarnabe/stylish/wiki/CSS-namespaces), and the example URL set.

The rules userstyles.org uses for determining a category are as follows:

1. If XUL is the default namespace, the style is an "app" style.
2. If there are no @-moz-document rules, the style is a "global" style.
3. If any of the @-moz-document rules are for the chrome, about, or x-jsd protocols, the style is an "app" style.
4. If any of the @-moz-document rules are of "url-prefix" type and apply to the entirety of the http, https, ftp, file, data, or chm:file protocols, the style is a "global" style.
5. Otherwise, the style is a "site" style.

Global styles do not receive a subcategory. For other styles, the site first tries to get an affected URL. The example URL is used for this, assuming it matches any of the @-moz-document rules. If no example URL is set, a value from the @-moz-document rules is used.

For site styles, the domain of affected URL gets stripped (e.g. a URL of http://www.example.com becomes "example") and that is the subcategory.

For app styles, the URL is checked against a map of common URL prefixes and the resulting value is the subcategory. If the URL does not match any common prefixes, the subcategory is "browser".