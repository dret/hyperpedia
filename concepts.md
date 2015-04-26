# Hyperpedia Concepts

This is a necessarily fuzzy and incomplete collection of information that can be associated with link in hypermedia scenarios.

This is _not_ an attempt to define the complete and strictly typed &uuml;bermodel for hypermedia.


## Target Identification

Links establish connections across resources, and thus need ways to identify the linked resources. On the Web, the identification mechanism is the [Uniform Resource Identifier (URI)](http://tools.ietf.org/html/rfc3986), or its internationalized variant, the [Internationalized Resource Identifier (IRI)](http://tools.ietf.org/html/rfc3986).

In both cases, identification is about a _resource_, and optionally about a [_resource fragment_](https://tools.ietf.org/html/rfc3986#section-3.5). If a resource fragment is specified, then the interpretation of the fragment identifier depends on the media type of the representation. This aspect gets a bit tricky if a resource is available in various representations, because the fragment identifier then should always identify the same logical fragment, but making sure that this is the case can be tricky, in particular if links are created by parties other than the resource provider.


## Link Relation

[Web Linking (RFC 5988)](http://tools.ietf.org/html/rfc5988)

is affected by _directionality_

## Resource Role

[W3C's XML Linking Language (XLink)](formats/XLink.md)

## Target Resource Type

[Internet Media Type](https://tools.ietf.org/html/rfc6838)

## Human-Readable Label(s)

includes Internationalization (I18N) issues ([Language Tags and Locale Identifiers for the World Wide Web](http://www.w3.org/TR/ltli/))

## Traversal Hints

for example, which [HTTP](http://tools.ietf.org/html/rfc7231) method to use

a [URI Template](http://tools.ietf.org/html/rfc6570), possibly with a description of the variables

is affected by _directionality_

## Topology

Binary or more than two participating resources

## Directionality

How is the link directed 

