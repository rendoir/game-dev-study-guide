# Design Patterns
## Creational
### Abstract Factory  
Provide an interface for **creating families of related or dependent objects** without specifying their concrete classes.  
The factory itself is abstract. To actually use it, there must be a concrete factory that implements the abstract one. The factory is then able to create concrete objects that extend the abstract objects. The factory can create **multiple different types of related objects** (e.g., a gasoline car factory can create an engine and transmission for a car while an electric car factory also creates both but as different concrete classes that extend either the engine or transmission abstract class).  
Like a factory but everything is encapsulated: the method that orders the object, the factories that build the object, and the final objects.
```cpp
AbstractFactory factory = ConcreteFactory();
AbstractObject object = factory.makeObject();
object.part.print();
```

### Builder  
Separate the construction of a complex object from its representation so that the same construction process can create different representations. Used for **incremental construction** of objects (i.e., step-by-step).

### Factory method  
Define an **interface for creating an object**, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.  
```cpp
Color.makeRGB(float red, float green, float blue);
```

### Object pool  
Object pooling can offer a significant performance boost; it is most effective in situations where the cost of initializing a class instance is high, the rate of instantiation of a class is high, and the number of instantiations in use at any one time is low.  
```cpp
Pool pool = new Pool(size);
Object object = pool.acquireObject();
pool.releaseObject(object);
```

### Prototype  
Specify the kinds of objects to create using a prototypical instance, and create new objects by **copying** (cloning) this prototype.  
```cpp
Vector3 original = new Vector3(1.0, 2.5, 3.0);
Vector3 copy = original.clone();
```

### Singleton  
Ensure a **class has only one instance**, and provide a **global point of access** to it.  
The single instance is a **private static attribute**. The accessor function is a public static method. The constructor is private. Lazy instantiation is desirable (initialize in the first access).
```cpp
class Singleton {
public:
    static Singleton& getInstance() {
        static Singleton instance;
        return instance;
    } 
};

Singleton instance = Singleton.getInstance();
```

## Structural
### Adapter  
Convert the interface of a class into another interface clients expect. Adapter lets classes work together that couldn't otherwise because of **incompatible interfaces**.
```cpp
// LegacyRectangle expects x1,y1,width,height
Rectangle rectangle = Adapter.getRectangle(x1,y1,x2,y2);
```

### Bridge  
Decouple an abstraction from its implementation so that the two can **vary independently**. Proposes refactoring cases of **exponentially explosive inheritance** hierarchy into two orthogonal hierarchies – for example, one for platform-independent abstractions, and the other for platform-dependent implementations.

### Composite  
Compose objects into tree structures to represent whole-part hierarchies. Composite lets clients treat **individual objects and compositions of objects** uniformly enabling **recursive composition**.

### Decorator  
**Attach additional responsibilities to an object dynamically**. Decorators provide a flexible alternative to subclassing for extending functionality.  
Client-specified embellishment of a core object by **recursively wrapping** it.  
![Decorator](https://sourcemaking.com/files/v2/content/patterns/Decorator__1.png)
```cpp
Interface* object = new Decorator3(
    new Decorator2(
        new Decorator1(
            new Core())));
object->doStuff();
```

### Facade  
Provide a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use. **Wrap a complicated subsystem with a simpler interface**.  

### Flyweight  
**Use sharing to support large numbers of fine-grained objects efficiently**.  
1. Divide the target class's state into: shareable (intrinsic) state, and non-shareable (extrinsic) state.
2. Remove the non-shareable state from the class attributes, and add it the calling argument list of affected methods.
3. Create a Factory that can cache and reuse existing class instances.
4. The client must use the Factory instead of the new operator to request objects. The client must look-up or compute the non-shareable state, and supply that state to class methods.
![Flyweight](https://dzone.com/sites/all/files/flyweight_pattern.png)

### Private Class Data  
Creates a **data class** to store the attributes so that they are **private**, even from the main class. The main class has an instance of the data class.

### Proxy  
Provide a surrogate or placeholder for another object to control access to it.  
Use an extra level of **indirection** to support distributed, controlled, or intelligent access.  
Add a wrapper and delegation to protect the real component from undue complexity.  

## Behavioral
### Chain of responsibility  
Establishes a **pipeline** for processing an object.  
![ChainResponsibility](https://sourcemaking.com/files/v2/content/patterns/Chain_of_responsibility__.png)

### Command
**Encapsulate a request as an object**, thereby letting you parametrize clients with different requests, queue or log requests, and support undoable operations.  
Promote "invocation of a method on an object" to full object status. Support for object-oriented callbacks.  
Decouples sender from receiver.  
```cpp
Bulb *bulb = new Bulb(); // Receiver

Command *turnOn = new TurnOn(bulb);
Command *turnOff = new TurnOff(bulb);

RemoteControl *remote = new RemoteControl(); // Sender
remote->submit(turnOn); // Calls command->execute();
remote->submit(turnOff); // Which calls bulb->turnOff();
```

### Interpreter
Given a **language**, define a representation for its grammar along with an interpreter that uses the representation to interpret sentences in the language.  
Map a domain to a language, the language to a grammar, and the grammar to a hierarchical object-oriented design.  
![Interpreter](http://coursegalaxy.com/designpatterns/interpreter/images/interpreter_structure.jpg)

### Iterator
Provide a way to **access** the elements of an aggregate object sequentially without exposing its underlying representation.  
![Iterator](https://sourcemaking.com/files/v2/content/patterns/Iterator.png)

### Mediator
Define an **object that encapsulates how a set of objects interact**. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently.  
Design an intermediary to decouple many peers.  
Promote the many-to-many relationships between interacting peers to "full object status".  
![Mediator](https://upload.wikimedia.org/wikipedia/commons/9/92/W3sDesign_Mediator_Design_Pattern_UML.jpg)

### Memento
Without violating encapsulation, capture and externalize an object's **internal state** so that the object can be **returned to this state later**.  
![Memento](https://sourcemaking.com/files/v2/content/patterns/Memento.png)
- Originator - the object that knows how to save itself.
- Caretaker - the object that knows why and when the Originator needs to save and restore itself.
- Memento - the lock box that is written and read by the Originator, and shepherded by the Caretaker.

### Null Object
The intent of a Null Object is to **encapsulate the absence of an object** by providing a substitutable alternative that offers suitable default "do nothing" behavior.
```cpp
Object nullObject = new NullObject();
nullObject.execute(); // Does nothing
```
![NullObject](https://sourcemaking.com/files/v2/content/patterns/Null_Object2.png)

### Observer
Define a one-to-many dependency between objects so that when one **object changes state**, all its **dependents are notified** and updated automatically.  
![Observer](https://sourcemaking.com/files/v2/content/patterns/Observer.png)
1. Define a list of observers in the subject class
2. On observer object creation, attach to the subject (add to list)
3. Every time the state changes, notify all observers

### State
Allow an object to **alter its behaviour when its internal state changes**. The object will appear to change its class.  
Used to implement an **object-oriented state machine**.  
![State](https://web.fe.up.pt/~arestivo/presentation/assets/gamepatterns/state.svg)

### Strategy
Define a **family of algorithms**, encapsulate each one, and make them **interchangeable**. Strategy lets the algorithm vary independently from the clients that use it.
![Strategy](https://web.fe.up.pt/~arestivo/presentation/assets/gamepatterns/strategy.svg)

### Template Method
Define the **skeleton of an algorithm** in an operation, deferring some steps to client subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.
```php
abstract class Builder
{
    // Template method
    final public function build()
    {
        $this->test();
        $this->lint();
        $this->assemble();
        $this->deploy();
    }

    abstract public function test();
    abstract public function lint();
    abstract public function assemble();
    abstract public function deploy();
}
```

### Visitor
Represent an **operation to be performed on the elements of an object structure**. Visitor lets you define a new operation without changing the classes of the elements on which it operates.
![Visitor](https://sourcemaking.com/files/v2/content/patterns/Visitor1.png)
