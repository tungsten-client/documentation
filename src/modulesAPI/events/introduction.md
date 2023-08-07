# Events
Tungsten uses [jMessenger](https://github.com/0x3C50/jMessenger) for its event system.

### Registering event subscribers
Any class can be registered as an event subscriber as long as it contains a function annotated with `@MessageSubscription`.

To register it, add `Tungsten.eventManager.registerSubscribers(instance)` to your init function on any listener classes. (`GenericModule` already runs it for you)

### Handling an event
As mentioned above, *any class can be registered as an event subscriber as long as it contains a function annotated with `@MessageSubscription`*.

But what actually is `@MessageSubscription`?

`@MessageSubscription` is used to define an event handler. It has one parameter:
- priority (optional) - The priority at which an event is run (default: 0)

The event handled by the function is determined by the event type in the parameters.

The general syntax for defining a handler looks like this:
```java
@MessageSubscription(priority = 2) // lower num goes first
void onSomething(SomeEvent event)
```

### Example
```java
public class EventExample extends GenericModule {
    public ExampleModule() {
        super("EventExample", "Event example module description.", "Default");
    }

    @MessageSubscription
    void onPlayerMove(PlayerMoveEvent event) {
        System.out.printf(
            "Move type: %s, Requested Delta: %s%n",
            event.type,
            event.requestedDelta
        );
    }
}
```

---

Check the [events package](https://github.com/tungsten-client/tungsten/tree/main/src/main/java/org/tungsten/client/event) to see all available events that you can use.