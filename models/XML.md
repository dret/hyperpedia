# Extensible Markup Language (XML)

The _Extensible Markup Language (XML)_ is a profile of [SGML](http://en.wikipedia.org/wiki/Standard_Generalized_Markup_Language) that has been designed for ease of use on the Web. While XML is designed to represent structured information, the concrete vocabulary used in XML documents is not part of XML itself, but instead defined by vocabularies using languages such as DTD or XSD. Because of this, XML itself has very little built-in semantics, and thus is rather rudimentary in terms of hypermedia features.

XML currently exists in two versions ([XML 1.0](http://www.w3.org/TR/xml/) and [XML 1.1](http://www.w3.org/TR/xml11/)), but these versions [only differ in ways that do not matter for their hypermedia features](http://www.w3.org/TR/xml11/#sec-xml11), and thus they are both covered in the same format description.


## External Entities

The concept of [external entities](http://www.w3.org/TR/xml/#sec-external-ent) in XML is used in three different places where XML documents can refer to URI-identified resources:

* The [document type declaration](http://www.w3.org/TR/xml/#sec-prolog-dtd) may point to a schema for a document that is defined in a [Document Type Definition (DTD)](http://www.w3.org/TR/xml/#dt-doctype). A [validating processor](http://www.w3.org/TR/xml/#proc-types) may use such a reference to retrieve the DTD and use it for validating the XML document that referred to the DTD.

* An [entity reference](http://www.w3.org/TR/xml/#sec-references) referring to a _parsed entity_ that was [declared](http://www.w3.org/TR/xml/#sec-entity-decl) as an [external entity](http://www.w3.org/TR/xml/#sec-external-ent) will be resolved by retrieving the referenced [parsed entity](http://www.w3.org/TR/xml/#TextEntities), and replacing the entity reference with the retrieved parsed entity. This mechanism thus defines _transclusion_ for XML content.

* An [entity reference](http://www.w3.org/TR/xml/#sec-references) referring to an _unparsed entity_ that was [declared](http://www.w3.org/TR/xml/#sec-entity-decl) as an [external entity](http://www.w3.org/TR/xml/#sec-external-ent) establishes a relationship between the XML document and the referenced entity. However, generic XML processors usually will not retrieve unparsed entities, as they do not contain XML-processable content.

All of these places have deep roots in the SGML history of XML, and many XML-based formats do not use any of them, but instead alternative methods to achieve similar goals.


## Namespace URIs

Even though [XML Namespaces](http://www.w3.org/TR/xml-names/) are neither part of XML, nor intended to be used as links, they are used in many XML vocabularies and use URIs, and thus may be worth mentioning briefly.

XML Namespace URIs are _only_ intended as identifiers and thus the only meaningful operation used on them is [comparing them](http://www.w3.org/TR/xml-names/#NSNameComparison). Any other operation, including using the URI as a link and dereferencing it, is outside of the scope of XML Namespaces as they are intended.
