With an event-driven system, the capture, communication, processing, and persistence of events are the core structure of the solution. This differs from a traditional request-driven model.

An event is any significant occurrence or change in state for system hardware or software. The source of an event can be from internal or external inputs.

[Event-driven architecture](https://www.redhat.com/en/topics/integration/what-is-event-driven-architecture) enables minimal coupling, which makes it a good option for modern, distributed application architectures.

Event-driven architecture is made up of event producers and event consumers. An event producer detects or senses an event and represents the event as a message. It does not know the consumer of the event, or the outcome of an event.

After an event has been detected, it is transmitted from the event producer to the event consumers through event channels, where an event processing platform processes the event asynchronously.

An event driven architecture may be based on either a pub/sub model or an event stream model.

The pub/sub model is based on subscriptions to an event stream. With this model, after an event occurs, or is published, it is sent to subscribers that need to be informed.

This differs from an event streaming model where event consumers don’t subscribe to an event stream. Instead, they can read from any part of the stream and can join the stream at any time.

Events are captured as they occur from event sources such as Internet of Things (IoT) devices, applications, and networks, allowing event producers and event consumers to share status and response information in real time.