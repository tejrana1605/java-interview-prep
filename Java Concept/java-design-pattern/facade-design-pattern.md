# Facade Design Pattern
The Facade Design Pattern is a structural pattern that provides a simplified, high-level interface to a complex system of classes, libraries, or frameworks. It aims to ease interaction by hiding the internal complexities, reducing the number of interactions needed and making the system easier to use and maintain.

### Key Points:

- Simplifies client interaction by providing a unified, higher-level interface.

- Hides complexities of subsystems and internal interactions.

- Promotes loose coupling between clients and subsystems.

- Encapsulates complex system intricacies, providing a clear, easier-to-understand API.

### Real-Life Example:
Using a home theater system:

- Instead of manually turning on each component—TV, DVD player, speakers, amplifier—the facade offers a simple "Watch Movie" method.

- Internally, the facade manages all subsystem components, coordinating their startup and configuration steps.

### Java Example: Pizza Toppings

```java
// Subsystem classes
class DVDPlayer {
    public void on() { System.out.println("DVD Player on"); }
    public void play() { System.out.println("DVD Player playing"); }
}

class Projector {
    public void on() { System.out.println("Projector on"); }
    public void setInput() { System.out.println("Projector input set"); }
}

class SoundSystem {
    public void on() { System.out.println("Sound System on"); }
    public void setVolume() { System.out.println("Sound volume set"); }
}

// Facade
class HomeTheaterFacade {
    private DVDPlayer dvd;
    private Projector projector;
    private SoundSystem sound;

    public HomeTheaterFacade(DVDPlayer dvd, Projector projector, SoundSystem sound) {
        this.dvd = dvd;
        this.projector = projector;
        this.sound = sound;
    }

    public void watchMovie() {
        dvd.on();
        dvd.play();
        projector.on();
        projector.setInput();
        sound.on();
        sound.setVolume();
        System.out.println("Movie started");
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        DVDPlayer dvd = new DVDPlayer();
        Projector projector = new Projector();
        SoundSystem sound = new SoundSystem();

        HomeTheaterFacade homeTheater = new HomeTheaterFacade(dvd, projector, sound);
        homeTheater.watchMovie();
    }
}
```

### Benefits:
- Simplifies complex interactions.

- Promotes loose coupling by hiding subsystem complexities.

- Improves system maintainability.

- Encapsulates behavior, making it easier to refactor or extend.

### Typical use cases:

- Simplifying APIs of complex libraries or frameworks.

- Managing interactions in multi-layered architectures.

- Working with legacy systems, providing a clean interface.

In summary, the Facade pattern is a strategic way to make large, complex systems more accessible and easier to maintain by providing a unified, simplified interface.


**[Back To Structural Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/structural-design-pattern.md#structural-design-patterns)**