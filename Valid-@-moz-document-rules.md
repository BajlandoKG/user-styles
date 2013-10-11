## Domain
Domain rules should just be the domain name, without protocol, port, or wildcards. A domain rule will affect all pages on that domain and all of its subdomains.

**Valid:**
```css
@-moz-document domain(example.com)
```
```css
@-moz-document domain(www.example.com)
```

**Invalid:**
```css
@-moz-document domain(*.example.com)
```
```css
@-moz-document domain(http://www.example.com/)
```
```css
@-moz-document domain(example.com:80)
```

## URL
URL rules should contain a URL you want to affect, including protocol. Wildcards are not permitted.

**Valid:**
```css
@-moz-document url(http://www.example.com/page.html)
```

**Invalid:**
```css
@-moz-document url(www.example.com/page.html)
```
```css
@-moz-document url(example.com)
```
```css
@-moz-document url(http://www.example.com/*)
```

## URL prefix
URL prefix rules should contain the start of URLs you want to affect, including protocol. Wildcards are not permitted.

**Valid:**
```css
@-moz-document url-prefix(http://www.example.com/)
```
```css
@-moz-document url-prefix(http://www.example.)
```
```css
@-moz-document url-prefix(http:)
```

**Invalid:**
```css
@-moz-document url-prefix(www.example.com/page.html)
```
```css
@-moz-document url-prefix(example.com)
```
```css
@-moz-document url-prefix(http://*.example.com/)
```

## Regexp

Regexp rules should be a valid regular expression which will be tested against the entire URL. Regexps must be enclosed in quotes. Backslashes must be escaped according to CSS rules. Regexp wildcards are permitted.

**Valid:**
```css
@-moz-document regexp("http://(www|blog)\\\\.example\\\\.com/.*")
```