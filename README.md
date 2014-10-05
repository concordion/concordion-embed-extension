This [Concordion](http://www.concordion.org) extension adds an `embed` command that embeds HTML in the Concordion output. It is similar to the [echo command](http://www.concordion.org/dist/1.4.4/spec/concordion/command/echo/Echo.html), except that it does not escape HTML text.

The [demo project](http://github.com/concordion/concordion-embed-extension-demo) demonstrates this extension.

# Installation

To install the extension with no namespace declarations, either annotate the fixture class with:

```java
    @Extensions(EmbedExtension.class)
```

or set the system property `concordion.extensions` to `org.concordion.ext.EmbedExtension`

# Usage

To use the `embed` command, add an attribute named `embed` using the namespace `"urn:concordion-extensions:2010"` to an element in your Concordion HTML. For example:

```html
    <html xmlns:concordion="http://www.concordion.org/2007/concordion"
        xmlns:ext="urn:concordion-extensions:2010">

    ....
    <span ext:embed="methodThatReturnsHtml()"/>
    ...
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
* [Demo project](http://github.com/concordion/concordion-embed-extension-demo)