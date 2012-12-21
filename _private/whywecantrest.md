Why we can't REST
=================
There has been considerable debate over the years on the applicability of Roy Fielding's Representational
State Transfer architectural style to the implementation of web applications. Most of it disregards
the distinction that REST is a style, not an architecture, and skips directly to analyzing how it
affects implementation concerns (e.g. "Is a certain API RESTful?"). This leaves a gap in the conceptual
model of developers trying to write code: the style should influence the architecture, and the
architecture should inform the implementation. With the lack of a well-defined architecture built on core
concepts of the REST style, the opposite happens in reality: web application code tends
to describe ad-hoc architectures that reflect the developer's current understanding of the style's
constraints. The problem with this lack of a REST-centric architecture is further compounded by additional
issues.

1. The MVC architecture
-----------------------
The current predominant architecture for web applications is Model View Controller. It focuses on separating
the three concerns of modelling the domain knowledge, presenting it to the user and handling user controls.
Its core concepts allow for implementations that conform to the REST style, but they don't map very well to
Fielding's concepts, and the architecture doesn't explicitly address the Fielding constraints.
Furthermore, there are subtle elements to its approach that have adverse effects on REST compliance.
While these effects can be easily overcome by developers experienced with both MVC and REST,
they're an obstacle for newcomers trying to understand the Fielding style through the lens of their MVC knowledge.

Consider the MVC architecture when applied to web apps: it represents the user as an actor that interacts
directly with the controller component. The controller then instructs the model to change its state, and
querries it for relevant data. It then provides this data to the view component, which prepares it for
presentation back to the user. The architecture completely disregards the networked aspect of web applications
by ignoring the client as a component and treating it as a simple communication interface between the user
and the controller. Effectively, the user requests documents from the controller, which in turns
instructs the view to provide them.

As such, the MVC architecture lacks the proper concepts to model key constraints of the Fielding style,
particularly the ones dealing with the communication between client and server.
Consequently, someone trying to understand this style based only on experience with MVC will rely on a mental
model that, while not being entirely adverse, doesn't "go with the grain".

2. Concrete examples that are not instructive
---------------------------------------------
One solution would be to warn new students of REST to not try to map Fielding's concepts to MVC concepts.
That would leave them having to grok abstract concepts (at one level higher than that of software architectures)
without anything concrete to relate to. The most popular advice given at this point is to consider
the structure of the World Wide Web. This is well intentioned; after all, the web and REST have been
developped in a parallel symbiosis. At the same time that he was working on formalizing Representational
State Transfer, Fielding was the primary architect for the HTTP/1.1 and related RFCs and co-founded the
Apache Foundation that provided the most popular web server. His architectural style had the purpose of capturing
the most desirable elements of the then-emerging web, while HTTP/1.1 et. al. were updates to the
web architecture informed by the REST style.

However, the architecture of the WWW is a poor example for the architecture of web applications. The
web conforms to the Fielding constraints mainly through the specification of its protocol (HTTP) and resource
identification (URI). But web applications use these mechanisms as building blocks in their own systems,
and this difference in abstraction level often makes drawing parallels awkward. More concretely, it's not
obvious how to draw advice on designing the communication between clients and servers from the
communication protocol of the web architecture, HTTP.

3. Implementation examples that are largely incorrect
-----------------------------------------------------
Mystified by the most popular Fielding architecture available, a new student of the Fielding style could
try to find inspiration one abstraction level below, in existing allegedly-RESTful implementations.
Many of these APIs though have been wrapped in marketing buzzwork though, and as a consequence there
is a vast body of discussion dissecting them and assessing their actual RESTfulness. Discussions are
often heated, and each argument is only as valid/valuable as the understanding its proponent has of REST
(which is of course always presented as authoritative). The situation is so confusing that the community
generally agrees the term REST has been irrecoverably distorted. The currently proposed rebranding is
Hypermedia API, but there are serious problems with that label so this work will generally use
"Fielding style" to refer to the architectural style Fielding defines in his PhD disertation.

To backtrack, the large majority of systems branded as RESTful violate some constraints of the Fielding style.
Most often they will focus on using proper HTTP verb semantics and resource-centric URLs while ignoring
the remaining constraints. The architectures can certainly be well constructed and useful, but the
Fielding style is very clearly defined by a sole authority, and those APIs are not architected according
to that style (the most common culprit is non-compliance with the hypermedia constraint). This is not
immediately obvious to a novice, so not only are these implementation examples not useful, they are
actually misleading.

The first step
--------------
Given these problems with the current situation, the best approach to promote proper understanding of
the Fielding architectural style among web developers is to define an architecture that properly
conforms to the style's constraints. Such an architecture will consider all the parts of the system
that the style concerns itself with (server, network, client), while prescribing only enough structure
to support the Fielding constraints. For example, it would not define the server's data model nor the
client architecture, but it would clearly specify how those parts should interact with the more
constrained elements (similarly to how MVC does not structure the model but it constrains
it to interface only with the controllers and not the views). Since the Fielding style is nothing more
than a collection of constraints that architectures should fulfill, many different designs can fit the style.
Hopefully in the near future we'll see a proliferation of efforts to define compliant web application
architectures so that we can start having discussions on REST at the proper level: that of
architectures not implementations.
