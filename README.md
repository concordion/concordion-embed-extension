[![Build Status](https://travis-ci.org/concordion/concordion-embed-extension.svg?branch=master)](https://travis-ci.org/concordion/concordion-embed-extension)
[![Maven Central](https://img.shields.io/maven-central/v/org.concordion/concordion-embed-extension.svg)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22org.concordion%22%20AND%20a%3A%22concordion-embed-extension%22)
[![Apache License 2.0](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)


This [Concordion](http://www.concordion.org) extension adds an `embed` command that embeds HTML in the Concordion output. It is similar to the [echo command](http://www.concordion.org/dist/1.4.4/spec/concordion/command/echo/Echo.html), except that it does not escape HTML text.

# Installation
The extension is available from [Maven Central](http://search.maven.org/#artifactdetails%7Corg.concordion%7Cconcordion-embed-extension%7C1.2.0%7Cjar).</a>

# Usage

To add the extension with no namespace declarations, either annotate the fixture class with:

```java
    @Extensions(EmbedExtension.class)
```

or set the system property `concordion.extensions` to `org.concordion.ext.EmbedExtension`

## HTML

For HTML format specifications, to use the `embed` command, add an attribute named `embed` using the namespace `"urn:concordion-extensions:2010"` to an element. For example:

```html
    <html xmlns:concordion="http://www.concordion.org/2007/concordion"
        xmlns:ext="urn:concordion-extensions:2010">

    ....
    <span ext:embed="methodThatReturnsHtml()"/>
    ...
```  

## Markdown

For Markdown format specifications, you need to declare the `ext` namespace in the Concordion fixture:

``` java
@ConcordionOptions(declareNamespaces={"ext", "urn:concordion-extensions:2010"})
```

The `embed` command can then be used within the Markdown spec, eg:

```markdown
[-](- "ext:embed=getDetails()")
```

## Declaring additional namespaces

If the HTML fragment includes elements or attributes with a namespace prefix, the additional namespaces must be declared, both in the HTML specification, and to the extension. The easiest way is to use the `@Extension` annotation on an `EmbedExtension` instance field within the fixture class.

For example, to map the `myns` prefix to the `http://com.myco/myns` namespace:

```java
        @Extension
        public ConcordionExtension extension =
            new EmbedExtension().withNamespace("myns", "http://com.myco/myns");
```

# Further info

* [Specification](http://concordion.github.io/concordion-embed-extension/spec/Embed.html)
* [API](http://concordion.github.io/concordion-embed-extension/api/index.html)
