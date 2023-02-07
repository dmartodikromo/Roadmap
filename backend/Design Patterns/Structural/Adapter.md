
Also known as wrapper. Convert the interface of a class into another interface the client expects. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.

Consider a captain that can only use rowing boats and cannot sail at all.

## Identification

Adapter is recognizable by a constructor which takes an instance of a different abstract/interface type. When the adapter receives a call to any of its methods, it translates parameters to the appropriate format and then directs the call to one or several methods of the wrapped object.

- First, we have interfaces `RowingBoat` and `FishingBoat`

```java
public interface RowingBoat {
  void row();
}

@Slf4j
public class FishingBoat {
  public void sail() {
    LOGGER.info("The fishing boat is sailing");
  }
}
```


- And captain expects an implementation of `RowingBoat` interface to be able to move

```java
public class Captain {

  private final RowingBoat rowingBoat;
  // default constructor and setter for rowingBoat
  public Captain(RowingBoat rowingBoat) {
    this.rowingBoat = rowingBoat;
  }

  public void row() {
    rowingBoat.row();
  }
}
```

- Now let's say the pirates are coming and our captain needs to escape but there is only a fishing boat available. We need to create an adapter that allows the captain to operate the fishing boat with his rowing boat skills.

```java
@Slf4j
public class FishingBoatAdapter implements RowingBoat {

  private final FishingBoat boat;

  public FishingBoatAdapter() {
    boat = new FishingBoat();
  }

  @Override
  public void row() {
    boat.sail();
  }
}
```

- Usage

```java
var captain = new Captain(new FishingBoatAdapter());
captain.row();
```

## Applicability

Use the Adapter pattern when

-   You want to use an existing class, and its interface does not match the one you need
-   You want to create a reusable class that cooperates with unrelated or unforeseen classes, that is, classes that don't necessarily have compatible interfaces
-   You need to use several existing subclasses, but it's impractical to adapt their interface by subclassing everyone. An object adapter can adapt the interface of its parent class.
-   Most of the applications using third-party libraries use adapters as a middle layer between the application and the 3rd party library to decouple the application from the library. If another library has to be used only an adapter for the new library is required without having to change the application code.

## Pros

- _Single Responsibility Principle_. You can separate the interface or data conversion code from the primary business logic of the program.
- _Open/Closed Principle_. You can introduce new types of adapters into the program without breaking the existing client code, as long as they work with the adapters through the client interface.

## Consequences

Class and object adapters have different trade-offs. A class adapter

-   Adapts Adaptee to Target by committing to a concrete Adaptee class. As a consequence, a class adapter won’t work when we want to adapt a class and all its subclasses.
-   Lets Adapter override some of Adaptee’s behavior since Adapter is a subclass of Adaptee.
-   Introduces only one object, and no additional pointer indirection is needed to get to the adaptee.

An object adapter

-   Lets a single Adapter work with many Adaptees, that is, the Adaptee itself and all of its subclasses (if any). The Adapter can also add functionality to all Adaptees at once.
-   Makes it harder to override Adaptee behavior. It will require subclassing Adaptee and making the Adapter refer to the subclass rather than the Adaptee itself.

-    The overall complexity of the code increases because you need to introduce a set of new interfaces and classes. Sometimes it’s simpler just to change the service class so that it matches the rest of your code.