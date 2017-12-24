# A Definition of Hypermedia APIs

*Hypermedia* refers to a model of providing and using information that is a combination of the two terms *Hypertext* and *Multimedia*.


## Hypertext

*Hypertext* refers to the fact that separate information units are made available as individually navigable resources, and that these resources are interconnected by *hyperlinks*. Consumers of hypertext follow navigation paths. For this to work, *links* must be clearly identified within individual resources, and they must be meaningfully navigable so that clients can make decisions which links to follow.

Interactions along links take clients from one resource to the next. Interactions can have whatever meaning the resource provider assigns to them, specifically they can be richer than just retrieving static data.


## Multimedia

*Multimedia* refers to the fact that the resources provided in a hypermedia context can use a variety of media types. Traditionally, it meant that information representation and display goes beyond simple text. Architecturally, it means that a hypermedia architecture must be capable of representing a variety of media types, and that clients potentially must be able to navigate through these various types.

This does not imply that all clients must be able to navigate all media types. It depends both on the resource providers and on application authors which media types they want to use for their needs, and which ones they choose to create or consume.


## Hypermedia APIs

Traditionally, hypermedia was conceived as a way for humans to interact with an information space. Consequently, many concepts in earlier hypermedia literature assume that human agents are using clients, which present rendered information to them, and allow them to navigate the information space.

More recently, the concept of hypermedia has been extended to cover APIs as well, where the assumption is that clients are not (necessarily) directly controlled by humans. In this case, hypermedia approaches need slightly different designs, because they cannot rely on humans reading "link labels" and then deciding which link to follow. Instead, these hypermedia APIs must represent hypermedia in a way that allows clients to autonomously navigate the information space in an attempt to accomplish their application goals.
