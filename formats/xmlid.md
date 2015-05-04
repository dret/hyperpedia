# xml:id

The [xml:id](http://www.w3.org/TR/xml-id/) specification is concerned with making fragment identifiers in [XML](XML.md) documents being self-describing at the document level. The problem with the original ID concept of XML is that in order to understand that some attribute is an identifier, it is necessary to interpret a document's schema (either a DTD or an XSD).

xml:id allows XML documents to make identifiers self-describing at the document level, so that by simply parsing an XML document, it is possible to determine which attributes are identifiers. This means that it is easier for inbound links to be anchored to XML document fragments, because this can be done without interpreting a document's schema; all that is needed is the document itself.

