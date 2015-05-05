# Hyperpedia Concepts

This is a necessarily fuzzy and incomplete collection of information that can be associated with link in hypermedia scenarios.

This is _not_ an attempt to define the complete and strictly typed &uuml;bermodel for hypermedia.


## Target Identification

Links establish connections across resources, and thus need ways to identify the linked resources. On the Web, the identification mechanism is the [Uniform Resource Identifier (URI)](http://tools.ietf.org/html/rfc3986), or its internationalized variant, the [Internationalized Resource Identifier (IRI)](http://tools.ietf.org/html/rfc3986).

In both cases, identification is about a _resource_, and optionally about a [_resource fragment_](https://tools.ietf.org/html/rfc3986#section-3.5). If a resource fragment is specified, then the interpretation of the fragment identifier depends on the media type of the representation. This aspect gets a bit tricky if a resource is available in various representations, because the fragment identifier then should always identify the same logical fragment, but making sure that this is the case can be tricky, in particular if links are created by parties other than the resource provider.

_Outgoing links_ generally follow two patterns:

* If they are linking the host resource as a whole, they are at the highest logical level of that resource, in some special section for establishing these kinds of resource-level links, or may even be completely out-of-line and transported in external channels such as an HTTP "Link" header field.

* If they are linking a fragment of the host resource, they often are embedded into the host resource in a way that encompasses the fragment of the host resource that is the subresource for the outgoing link.

_Incoming links_ generally follow two analogous patterns:

* If the link target the complete resource, no specific additional information is required, and just identifying the resource by URI is enough.

* If the link target is a subresource, then the URI will have a fragment identifier. Depending on the resource representation, this may or may not require the resource to provide a specific anchoring mechanism. In [HTML](formats/HTML.md), for example, fragments refer to names and thus these names must be specified in the target resource in order for the subresource to be name-addressable. In [plain text](https://tools.ietf.org/html/rfc2046#section-4.1), on the other hand, [fragment identifiers](https://tools.ietf.org/html/rfc5147) use line and character addressing, and thus subresources can be identified without the need for explicit anchors in the target resource.


## Link Relation Type

Hypermedia links serve a certain purpose, i.e. a client choose to follow links based on client goals, and whether following certain links is necessary to achieve those goals. The goal is something that is based on the context of the link, and on the particular client. _Link relations_ are one way of typing links, allowing them to be annotated with information about _why_ a client might want to follow a given link. Link relations should not be used express an expectation _what_ resource to expect as the link's target, instead they should only represent information about _why_ a client might want to follow a link.

[Web Linking (RFC 5988)](http://tools.ietf.org/html/rfc5988) is one standard on the Web that defines a simple framework for link relation identification, and also defines a way how links can be represented in an HTTP "Link" header field. Using this specification allows hypermedia links to be open and extensible in terms of which types of link relations can be represented.

[HTML](formats/HTML.md) and similar markup-based languages sometimes use element or attribute names to represent link relation types. While this has the advantage of being easily readable markup, the disadvantage is that the link relation types become hardcoded into the language's schema, which means that the set of supported link relation types is predefined and not extensible without changing the language itself.

Link relation information is affected by _directionality_. If a link format has notions of representing "forward" and "backward" links, then the link relation type much be annotated in a way that identifies the direction it applies to, because most link relation types do not represent symmetric relationships between resources.


## Human-Readable Label(s)

includes Internationalization (I18N) issues ([Language Tags and Locale Identifiers for the World Wide Web](http://www.w3.org/TR/ltli/))


## Target Resource Hints

A link itself should represent all the information that a client needs to decide whether it should or should not traverse the link, based on client goals. But that does not imply _what_ to expect as the target resource, it _only_ implies _why_ a client might decide to engage in a resource interaction. This is important because a link should not hardcode assumptions about what to expect when traversing the link, because this may change over time.

However, in some scenarios link authors may choose to represent information about the target resource. However, since these are mere assumptions made at _link authoring time_ (which can be very different from _link traversal time_), this information can merely serve as a _hint_ and may or may not turn out to be correct at link traversal time. Therefore, hints always should be optional and should be treated as information that may or may not be true when the link is traversed. Clients should always give preference to any resource information that results from link traversal, rather than assuming that the resource hint was correct.

Typical target resource hints include a resource's [Internet Media Type](https://tools.ietf.org/html/rfc6838), and more generally speaking, a typical set is the set of resource properties that can be used in [HTTP Content Negotiation](https://tools.ietf.org/html/rfc7231#section-5.3). These properties are the media type, the character set, the encoding, and the language.


## Traversal Hints

A link communicates to a client one possible hypermedia navigation, and the client might choose to follow a link based on client goals. However, depending on the type of navigation, it may be necessary to know additional rules that need to be followed when traversing the link. However, these rules will be specific to specific interaction with the target resource, which is not determined by the link itself, but instead by the [URI scheme](https://tools.ietf.org/html/rfc3986#section-3.1) of the target resource identifier, and possibly by the target resource itself.

The idea of _traversal hints_ is to give clients hints about _how_ to traverse a link. This may include information such as which [HTTP method](https://tools.ietf.org/html/rfc7231#section-4) to use, but may also include more specific information about how to interact with the target resource, such as a [URI Template](http://tools.ietf.org/html/rfc6570), possibly with a description of the variables.

Generally speaking, there are two major approaches to how traversal hints can be represented:

* Traversal hints can be _implicit_ in a link's type, so that the link itself already represents a hint as to how to traverse it. For example, [HTML forms](http://www.w3.org/TR/html401/interact/forms.html#submit-format) define two possible ways how to communicate the contents of a form, and while the choice between those two is made explicit (using the [_method_](http://www.w3.org/TR/html401/interact/forms.html#adef-method) attribute), the rules themselves are hardcoded in the HTML specification.

* Traversal hints can be _explicit_ in the link's representation, so that clients have to interpret and use them at runtime. For example, a [URI Template](http://tools.ietf.org/html/rfc6570) is one way how a link can specify how to compose the [query component](https://tools.ietf.org/html/rfc3986#section-3.4) of a URI when traversing a link.

Since traversal hints tell a client how to behave when following a link, they are affected by the _directionality_ and the _topology_ of a link, should those be concepts that are variable in a specific link model.


## Topology

While links usually are thought of to have two participating resources or subresources (the _source_ and the _target_), link models can also support other topologies. It is both possible to have _unary_ "links" (which also can be thought of as annotations, since "traversing" them is not a meaningful concept), or _n-ary_ links, where the link model supports more than two participating resources.

Some generalized link models such as [W3C's XML Linking Language (XLink)](formats/XLink.md) support n-ary links. While the exact design of those links depends on the language, it is important to note that for these kinds of links, typically more link metadata is required to make the link actionable. In typical n-ary link models, both the set of participating resources as well as the connecting _arcs_ (to choose the XLink term for this concept) between them need to be made explicit, so that clients know how to navigate such a structurally complex link.


## Resource Role

[W3C's XML Linking Language (XLink)](formats/XLink.md)


## Directionality

How is the link directed 

