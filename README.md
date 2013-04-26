Shallow XML parser for Node.js
===========

This parser allows you to parse XML documents that contains fragments that is
impossible to parse using "classical" parsing methods. For instance you have an
abstract HTML document provided by the 3rd party. The only thing you know about
this document is that it contains "something" inside `<body></body>` tag. You
have no idea if it's valid but your task is to extract this data and use it
for something else. You won't be able to parse this document (in case if it's invalid)
using classical XML parser.

Instead of doing it in classical way, shallow-xml uses a technique called
[shallow parsing](http://en.wikipedia.org/wiki/Shallow_parsing). Using regular expressions
it converts original xml - document into a list of tokens, trying to extract as much
useful information as possible, based on known structure defined by the developer.
Take a look on following XML document (OpenSocial gadget definition):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Module>
  <ModulePrefs title="Proxied Content Example" />
  <Content view="home">
    <ul>
      <li>111
      <li>222
      <li>333
    </ul>
  </Content>
</Module>
```

As you can see this xml document cannot be parsed using classical xml parser,
because HTML code that is placed inside `<Content></Content>` tag is invalid.
