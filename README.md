# Event Typology and literature references
The different types of events and literature references
<br>

*updates:*<br>
*15.06.2024: Addition discrete events*<br>
*09.06.2024: Addition pivotal events*<br>
*15.05.2024: Initial version*<br>
<br>

### Data event
* Data events describe the **state of an entity at a specific moment in time**. They may be produced at a certain rate or if the state changes. Every data event at least contains the whole state of the entity but may also include the old state to allow consumers to detect changes. Data events do not contain the reason for the change. [OTTO Consumer API Event Guidelines](https://api.otto.de/portal/guidelines/event-guidelines/concepts#data-events)

___


### Delta event
* Delta events contain just the properties that changed, so just enough detail, nothing more. [The Event-Carried State Transfer pattern (by Oskar uit de Bos 2021)](https://itnext.io/the-event-carried-state-transfer-pattern-aae49715bb7f)
* ECST messages that include  only the updated fields... [Learning Domain-Driven Design. Aligning Software Architecture and Business Strategy (by Vlad Khononov 2021) p317](https://www.oreilly.com/library/view/learning-domain-driven-design/9781098100124/)
* As indicated by Figure 8.5, cumbersome state modification determination is not the case when using PATCH. With a **partial update**, it is straightforward to determine what the fine-grained event-based outcome is for the use case, because it is clear exactly what changed. [Strategic Monoliths and Microservices by Vernon, Jaskula 2022 (by Vernon, Jaskula 2022) p194](https://www.informit.com/store/strategic-monoliths-and-microservices-driving-innovation-9780137355464)

___


### Discrete event
* Think of discrete events as significant (important) **facts that have happened**, and you have downstream consumers that want to act on this information. [Understanding stream and discrete events (by David Boyne 2024)](https://eda-visuals.boyney.io/visuals/understanding-stream-and-discrete-events)

___


### Domain event
* The term domain event describes an occurrence of something that **happened in the business domain**. The concept originates in Domain-Driven Design (DDD). The event’s name usually already carries a lot of semantic meaning and is used within the domain language to describe the domain’s processes. [OTTO Consumer API Event Guidelines](https://api.otto.de/portal/guidelines/event-guidelines/concepts#domain-events)
* As a default practice, consider every domain event **"private", only meant for internal consumption**. Only through deliberate exposure consumers get access to the events, similar to how APIs are used instead of direct database access. [The different types of events in event-driven systems Frank de Jonge 2022](https://blog.frankdejonge.nl/the-different-types-of-events-in-event-driven-systems/)
* The terminology that is used for the aggregate’s name, its data members, its actions, and its **domain events all should be formulated in the bounded context’s ubiquitous language**. [Learning Domain-Driven Design. Aligning Software Architecture and Business Strategy (by Vlad Khononov 2021) p134](https://www.oreilly.com/library/view/learning-domain-driven-design/9781098100124/)
* Asynchronous translation can be used to **intercept the domain events and convert them into a published language**, thus providing better encapsulation of the bounded context’s implementation details. [Learning Domain-Driven Design. Aligning Software Architecture and Business Strategy (by Vlad Khononov 2021) p194](https://www.oreilly.com/library/view/learning-domain-driven-design/9781098100124/)
* Finally, **sparingly use domain events for communication with external bounded contexts**. Consider designing a set of dedicated public domain events. [Learning Domain-Driven Design. Aligning Software Architecture and Business Strategy (by Vlad Khononov 2021) p325](https://www.oreilly.com/library/view/learning-domain-driven-design/9781098100124/)
* A domain event is something that happened in the domain that is relevant to other microservices **within the same bounded context**. [The Event-Carried State Transfer pattern (by Oskar uit de Bos 2021)](https://itnext.io/the-event-carried-state-transfer-pattern-aae49715bb7f)
* A Domain Event that is published outside your Bounded Context should be defined in your **Published Language**. [LinkedIn post (by Vaughn Vernon 2023)](https://www.linkedin.com/posts/vaughnvernon_dddesign-activity-7121926516568911873-Itb9/)
* I extremely dislike the split of "domain" and "integration" events.The split is highly misleading. All of them should be domain events and represent business facts. I prefer to split them into **internal and external** (or, as Nick Tune 🇺🇦, into **private and public**). [LinkedIn post (by Oskar Dudycz 2023)](https://www.linkedin.com/posts/oskardudycz_i-extremely-dislike-the-split-of-domain-activity-7119331094696476672-1x6r/)
* Examples of things that happen that might **not** be suitable to model as Domain Events:
    1. Something **technical** (a ButtonClicked, ExceptionThrown etc) happened that we want to record or handle, but it is not described in the ubiquitous language of our domain.
    2. Something that happened **outside of our bounded context**. This could a Domain Event in another system or a different bounded context. [What are Domain Events? Mattias Holmqvist 2020](https://web.archive.org/web/20221201162409/https://serialized.io/ddd/domain-event/)

___


### Event-carried state transfer
* If autonomy is your driving requirement -> consider **enrichment**. [DDD re-distilled (by Yoan Thirion 2020) slide51](https://speakerdeck.com/thirion/ddd-re-distilled?slide=51)
* De naam Event-carried State Transfer **(EST ?)** is gekozen om een beetje te contrasteren met REST. [De vier gezichten van EDA (by Koen Vanderkimpen 2022)](https://www.smalsresearch.be/de-vier-gezichten-van-eda/)
* Whether ECST messages **include complete snapshots or only the updated fields**, a stream of such events allows consumers to hold a local cache of the entities’ states and work with it. [Learning Domain-Driven Design. Aligning Software Architecture and Business Strategy (by Vlad Khononov 2021) p316](https://www.oreilly.com/library/view/learning-domain-driven-design/9781098100124/)

___


### Event notification
* The notification event is small and concise as it only **contains a reference** to the state that was changed. [The event notification pattern (by Oskar uit de Bos 2021)](https://medium.com/geekculture/the-event-notification-pattern-a62d48519107)
* Belangrijk in dit patroon, is dat de Events verder **geen toestand** bevatten. Als de ontvangers van het event dus willen weten wát er precies is veranderd aan de klantenfiche, of wát er besteld werd in het order, dan zullen ze toch actief initiatief moeten nemen om aan deze informatie te geraken. [De vier gezichten van EDA (by Koen Vanderkimpen 2022)](https://www.smalsresearch.be/de-vier-gezichten-van-eda/)
* The event notification **should not be verbose**: the goal is to notify the interested parties about the event, but the notification shouldn’t carry all the information needed for the subscribers to react to the event. [Learning Domain-Driven Design. Aligning Software Architecture and Business Strategy (by Vlad Khononov 2021) p313](https://www.oreilly.com/library/view/learning-domain-driven-design/9781098100124/)

___



### Mutation event

___


### Pivotal event
* Pivotal events indicate major changes in the domain and often form the boundary between one phase of the system and another. Pivotal events will typically **separate (a bounded context** in DDD terms). Pivotal events are identified with vertical blue painters tape (crossing all the swimlanes). [Event-Driven Solutions in Hybrid Cloud (by Jerome Boyer 2024)](https://jbcodeforce.github.io/eda-studies/event-storming/#concepts)


___


### Tombstone event
* Kafka even has a convention to signify deletions: a message **with a key but a null payload, also known as a tombstone**. This indicates that the record should be deleted. Due to compaction, all non-tombstone messages will eventually disappear, leaving nothing but the deletion record (and that can be auto-compacted as well). [Design patterns for asynchronous API communication (by Daniel Orner 2022)](https://stackoverflow.blog/2022/07/21/event-driven-topic-design-using-kafka/)


___
<br>
<br>

## Miscellaneous:

### When is an event NOT an event?
* So, when is an event **not** an event? [Ben Morris - Agile enterprise architecture 2020](https://www.ben-morris.com/when-is-an-event-not-an-event/)

___

### Data streams vs Event streams
* Wanneer gegevens over gebeurtenissen geen metadata bevatten spreken we over data en data streams (bijv. bij sensoren die alleen een pakket ruwe data leveren). Als er **wel contextgegevens** aanwezig spreken we over events en event streams (bijv. bij gebeurtenisgegevens die op basis van metakenmerken moeten worden geïnterpreteerd om verwerkt te kunnen worden). [Project Notificaties Architectuur p57](https://github.com/VNG-Realisatie/notificatieservices/blob/main/docs/achtergronddocumentatie/notificatieservices_architectuur.pdf)


___

### Event notification vs Event-carried state transfer
* Notification events: **less risk of data being out of sync** versus Event-carried state transfer: **higher risk of data being out of sync**. [EVENT TYPES by David Boyne](https://eda-visuals.boyney.io/visuals/event-types)


___
