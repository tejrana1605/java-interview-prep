
# Flyweight Design Pattern
The Flyweight Design Pattern is a structural design pattern aimed at minimizing memory usage by sharing internal state among multiple objects instead of creating numerous separate instances. It is especially beneficial when an application involves a large number of objects with similar properties.

**OR**
The Flyweight Pattern is a structural design pattern that helps reduce memory usage by sharing objects that are similar in nature.

Instead of creating multiple copies of identical or similar objects, you reuse shared instances (called flyweights).

**OR**

The flyweight design pattern is applied when producing many class objects. By sharing objects, the flyweight design pattern helps reduce pressure on memory, which is important for low memory devices like embedded systems and mobile devices. This is because every object takes up memory space. Before using the flyweight design pattern, the following elements must be considered:

- The program should generate many objects.

- The process of creating an object takes a lot of memory and might take some time.

- The external properties of an object must be determined by the client program.The properties of an object can be classified as internal or external.

We must separate Object attribute into intrinsic and extrinsic qualities to apply the flyweight pattern. While extrinsic characteristics are set by client code and are utilised for various purposes, intrinsic properties are what give an object its uniqueness. 

For example, an object Circle might have external properties such as color and width. We need to create a Flyweight factory that provides shared objects to implement the Flyweight pattern. Let us take an example where we need to draw something using lines and ovals. Thus, we shall own an interface Shape together with its tangible realisations, which are Line and Oval. Whereas Line has no intrinsic property, oval class will have one to decide whether to fill the oval with the specified colour or not.

```java
package com.journaldev.design.flyweight;  
import java.awt.Color;  
import java.awt.Graphics;  
 public interface Shape {     
 public void draw(Graphics g, int x, int y, int width, int height,  
 Color color);   
}  
```

Line.java

```java
package com.journaldev.design.flyweight;  
import java.awt.Color;   
import java.awt.Graphics;   
public class Line implements Shape {   
    public Line(){   
        System.out.println("Creating Line object");  
        //adding time delay   
        try {   
            Thread.sleep(2000);   
        }  
catch (InterruptedException e) {              
e.printStackTrace();          
}     
}     
@Override     
public void draw(Graphics line, int x1, int y1, int x2, int y2,               
Color color) {        
line.setColor(color);         
line.drawLine(x1, y1, x2, y2);    
}   
} 
```

Oval.java

```java
package com.journaldev.design.flyweight;   
import java.awt.Color;   
import java.awt.Graphics;   
public class Oval implements Shape {   
    //intrinsic property   
    private boolean fill;   
    public Oval(boolean f){   
        this.fill=f;   
        System.out.println("Creating Oval object with fill="+f);   
        //adding time delay   
        try {   
            Thread.sleep(2000);   
        } catch (InterruptedException e) {   
            e.printStackTrace();   
        }   
    }   
    @Override   
    public void draw(Graphics circle, int x, int y, int width, int height,   
            Color color) {   
        circle.setColor(color);   
        circle.drawOval(x, y, width, height);   
        if(fill){   
            circle.fillOval(x, y, width, height);   
        }     
}   
}  
```

### Flyweight Factory
We need to maintain a map of objects in the flyweight factory that client applications should not be able to access, as the flyweight factory will be utilised by client programs to instantiate the object. When a client program calls the HashMap to retrieve an instance of an object, the object should always be returned; if it cannot be located, a new object should be created, added to the Map, and then returned. When generating the Object, we must ensure that all the inherent attributes are considered. The code for our flyweight factory class is as follows.

```java
package com.journaldev.design.flyweight;   
import java.util.HashMap;   
public class ShapeFactory {   
    private static final HashMap<ShapeType,Shape> shapes = new   
HashMap<ShapeType,Shape>();   
    public static Shape getShape(ShapeType type) {   
        Shape shapeImpl = shapes.get(type);   
        if (shapeImpl == null) {   
            if (type.equals(ShapeType.OVAL_FILL)) {   
                shapeImpl = new Oval(true);   
            } else if (type.equals(ShapeType.OVAL_NOFILL)) {      
            shapeImpl = new Oval(false);      
        } else if (type.equals(ShapeType.LINE)) {     
            shapeImpl = new Line();       
        }     
        shapes.put(type, shapeImpl);      
    }     
  
    return shapeImpl;     
}   
    public static enum ShapeType{   
        OVAL_FILL,OVAL_NOFILL,LINE;   
    }   
}  
```

Take note of how the getShape function uses the Factory design, Java Composition (a shapes map), and Java Enum for type safety.

### Flyweight Design Pattern Client Example

An example programme that uses flyweight pattern implementation is shown below. Java DrawingClient.

DrawingClient.java

```java
package com.journaldev.design.flyweight;   
import java.awt.BorderLayout;   
import java.awt.Color;   
import java.awt.Container;   
import java.awt.Graphics;   
import java.awt.event.ActionEvent;   
import java.awt.event.ActionListener;   
import javax.swing.JButton;   
import javax.swing.JFrame;   
import javax.swing.JPanel;   
import com.journaldev.design.flyweight.ShapeFactory.ShapeType;   
public class DrawingClient extends JFrame{   
    private static final long serialVersionUID = -1350200437285282550L;   
    private final int WIDTH;   
    private final int HEIGHT;   
    private static final ShapeType shapes[] = { ShapeType.LINE,   
ShapeType.OVAL_FILL,ShapeType.OVAL_NOFILL };   
    private static final Color colors[] = { Color.RED, Color.GREEN, Color.YELLOW   
};   
    public DrawingClient(int width, int height){   
        this.WIDTH=width;   
        this.HEIGHT=height;   
        Container contentPane = getContentPane();   
        JButton startButton = new JButton("Draw");   
        final JPanel panel = new JPanel();   
        contentPane.add(panel, BorderLayout.CENTER);   
        contentPane.add(startButton, BorderLayout.SOUTH);   
        setSize(WIDTH, HEIGHT);   
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);   
        setVisible(true);   
        startButton.addActionListener(new ActionListener() {   
            public void actionPerformed(ActionEvent event) {   
                Graphics g = panel.getGraphics();   
                for (int i = 0; i < 20; ++i) {     
                Shape shape =   
ShapeFactory.getShape(getRandomShape());   
                    shape.draw(g, getRandomX(), getRandomY(),   
getRandomWidth(),   
                            getRandomHeight(), getRandomColor());   
                }   
            }   
        });   
    }   
    private ShapeType getRandomShape() {   
        return shapes[(int) (Math.random() * shapes.length)];   
    }   
    private int getRandomX() {   
        return (int) (Math.random() * WIDTH);   
    }   
    private int getRandomY() {    
    return (int) (Math.random() * HEIGHT);   
  
    }   
    private int getRandomWidth() {    
    return (int) (Math.random() * (WIDTH / 10));      
}   
    private int getRandomHeight() {       
    return (int) (Math.random() * (HEIGHT / 10));     
}   
    private Color getRandomColor() {      
    return colors[(int) (Math.random() * colors.length)];     
}   
    public static void main(String[] args) {      
    DrawingClient drawing = new DrawingClient(500,600);       
}   
}  

Output:

Creating Line object
Creating Oval object with fill=true
Creating Oval object with fill=false

```

### Example of flyweight

```java
// A Java program to demonstrate working of   
// FlyWeight Pattern with example of Counter   
// Strike Game   
import java.util.Random;   
import java.util.HashMap;   
// A common interface for all players   
interface Player   
{    
   public void assignWeapon(String weapon);    
   public void mission();   
}   
// Terrorist must have weapon and mission   
class Terrorist implements Player   
{    
   // Intrinsic Attribute     
  private final String TASK;    
   // Extrinsic Attribute    
   private String weapon;    
    public Terrorist()    
   {      
     TASK = "PLANT A BOMB";   
    }      
 public void assignWeapon(String weapon)     
 {      
     // Assign a weapon      
     this.weapon = weapon;    
   }    
   public void mission()    
   {     
      //Work on the Mission     
      System.out.println("Terrorist with weapon "     
                         + weapon + "|" + " Task is " + TASK);    
   }   
}   
// CounterTerrorist must have weapon and mission   
class CounterTerrorist implements Player   
{     
  // Intrinsic Attribute    
   private final String TASK;     
  // Extrinsic Attribute   
    private String weapon;    
   public CounterTerrorist()    
   {    
       TASK = "DIFFUSE BOMB";   
    }    
   public void assignWeapon(String weapon)     
  {       
    this.weapon = weapon;     
  }    
   public void mission()    
   {    
       System.out.println("Counter Terrorist with weapon "       
                       + weapon + "|" + " Task is " + TASK);     
  }   
}   
// Class used to get a player using HashMap (Returns   
// an existing player if a player of given type exists.   
// Else creates a new player and returns it.   
class PlayerFactory   
{   
    /* HashMap stores the reference to the object  
       of Terrorist(TS) or CounterTerrorist(CT).  */    
   private static HashMap <String, Player> hm =     
                       new HashMap<String, Player>();   
    // Method to get a player   
    public static Player getPlayer(String type)    
   {     
      Player p = null;      
     /* If an object for TS or CT has already been     
        created simply return its reference */     
      if (hm.containsKey(type))      
             p = hm.get(type);      
     else    
       {         
      /* create an object of TS/CT  */     
          switch(type)      
         {        
       case "Terrorist":             
      System.out.println("Terrorist Created");          
         p = new Terrorist();        
           break;        
       case "CounterTerrorist":            
       System.out.println("Counter Terrorist Created");        
           p = new CounterTerrorist();      
             break;         
      default :        
           System.out.println("Unreachable code!");       
        }         
      // Once created insert it into the HashMap      
         hm.put(type, p);     
      }       
    return p;     
  }   
}   
// Driver class   
public class CounterStrike   
{    
   // All player types and weapon (used by getRandPlayerType()    
   // and getRandWeapon()     
  private static String[] playerType =      
                 {"Terrorist", "CounterTerrorist"};      
 private static String[] weapons =     
    {"AK-47", "Maverick", "Gut Knife", "Desert Eagle"};       
 // Driver code      
 public static void main(String args[])   
    {          
 /* Assume that we have a total of 10 players   
          in the game. */     
      for (int i = 0; i < 10; i++)     
      {        
       /* getPlayer() is called simply using the class       
          name since the method is a static one */       
       Player p = PlayerFactory.getPlayer(getRandPlayerType());        
       /* Assign a weapon chosen randomly uniformly        
         from the weapon array  */         
      p.assignWeapon(getRandWeapon());       
        // Send this player on a mission       
        p.mission();     
      }      
 }    
   // Utility methods to get a random player type and    
   // weapon    
   public static String getRandPlayerType()   
    {      
     Random r = new Random();       
   // Will return an integer between [0,2)        
   int randInt = r.nextInt(playerType.length);      
     // return the player stored at index 'randInt'       
    return playerType[randInt];    
   }     
  public static String getRandWeapon()     
  {        
   Random r = new Random();          
 // Will return an integer between [0,5)       
    int randInt = r.nextInt(weapons.length);         
  // Return the weapon stored at index 'randInt'       
    return weapons[randInt];     
  }   
}


Output:

Counter Terrorist Created
Counter Terrorist with weapon Gut Knife| Task is DIFFUSE BOMB
Counter Terrorist with weapon Desert Eagle| Task is DIFFUSE BOMB
Terrorist Created
Terrorist with weapon AK-47| Task is PLANT A BOMB
Terrorist with weapon Gut Knife| Task is PLANT A BOMB
Terrorist with weapon Gut Knife| Task is PLANT A BOMB
Terrorist with weapon Desert Eagle| Task is PLANT A BOMB
Terrorist with weapon AK-47| Task is PLANT A BOMB
Counter Terrorist with weapon Desert Eagle| Task is DIFFUSE BOMB
Counter Terrorist with weapon Gut Knife| Task is DIFFUSE BOMB
Counter Terrorist with weapon Desert Eagle| Task is DIFFUSE BOMB
```

### Core Concepts:

* **Intrinsic State:** Shared, unchanging data stored in the flyweight object (e.g., color, shape type).

* **Extrinsic State:** Context-dependent data supplied from outside the flyweight (e.g., position, size) whenever needed.

* **Flyweight Factory:** Central class that manages flyweight objects and ensures sharing by returning existing instances if available.

### Java Example: Typeface and Character Flyweights
Suppose we're implementing a text editor that displays thousands of characters.

```java
// Flyweight interface
interface Character {
    void display(int size, String font);
}

// Concrete Flyweight
class ConcreteCharacter implements Character {
    private final char symbol; // intrinsic (shared) state

    public ConcreteCharacter(char symbol) {
        this.symbol = symbol;
    }

    @Override
    public void display(int size, String font) {
        // extrinsic state is provided here
        System.out.println("Displaying '" + symbol + "' with size " + size + " and font " + font);
    }
}

// Flyweight Factory
class CharacterFactory {
    private static final Map<Character, Character> characters = new HashMap<>();

    public static Character getCharacter(char symbol) {
        Character character = characters.get(symbol);
        if (character == null) {
            character = new ConcreteCharacter(symbol);
            characters.put(symbol, character);
        }
        return character;
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        String text = "Hello World!";
        int fontSize = 12;
        String fontType = "Arial";

        for (char c : text.toCharArray()) {
            Character character = CharacterFactory.getCharacter(c);
            character.display(fontSize, fontType);
        }
    }
}
```

### In this example:

- Each character (like 'H', 'e') is shared if identical, minimizing object creation.

- The shared ConcreteCharacter objects contain the intrinsic state (symbol), while extrinsic state (size, font) is supplied at call time.

- The CharacterFactory manages the shared objects, returning existing instances whenever possible.

### Benefits:
- Significant memory savings when managing a lot of similar objects.

- Improves performance in memory-critical environments.

- Facilitates code reusability and reduces object creation overhead.

### Limitations:
- Managing extrinsic state is crucial; passing large extrinsic data many times may diminish benefits.

- More complex to implement when objects have many intrinsic properties.

### Applications:
- Text editors (characters sharing fonts and sizes).

- Graphic design tools (shared shapes or icons).

- Large data visualization systems with many similar elements.

This pattern is very effective when you need to manage thousands of fine-grained objects with shared state efficiently.

**[Back To Creational Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/structural-design-pattern.md#structural-design-patterns)**