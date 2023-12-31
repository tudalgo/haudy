# Dokumentation von Java-QuellCode

!!! info "Information"
    In der Softwareentwicklung ist es wichtig, seinen Code ordentlich zu dokumentieren, damit es möglich ist, diesen ohne viel Aufwand zu verstehen.
    Dies hilft sowohl anderen, die mit Ihrem Code arbeiten oder ihn benutzen, als auch Ihnen selber, wenn Sie länger nicht mehr mit diesem gearbeitet haben.
    Die Dokumentation sollte dabei kurz erklären, was der Code macht und wie er zu benutzen ist.
    Es sollte aber nicht erklärt werden, wie genau der Code funktioniert, sondern dieser sollte als eine Blackbox, in welche man nicht genauer hineingucken kann, betrachtet werden.

* In Java werden JavaDoc Kommentare als standardisierte Methode benutzt um Code zu dokumentieren.
    * JavaDoc Kommentare haben dabei den Vorteil, dass IDEs sie automatisch anzeigen können und HTML Seiten aus ihnen generiert werden können.
* Jeder JavaDoc Kommentar beginnt dabei mit **/\*\*** und endet mit **\*/**.
  Jede neue Zeile beginnt mit einem **\***.
* JavaDoc Kommentare werden direkt über die zugehörige Klasse, Methode, etc. geschrieben.
* Wenn Sie in IntelliJ über einer Methode, Klasse, etc. **/\*\*** schreiben und dann **Enter** drücken, wird automatisch eine Vorlage für Sie erstellt.
* JavaDoc Kommentare sehen dabei z.B. wie folgt aus:

!!! example "Beispiel"
    ```java

    /**
     * Represents a game board that consists of a two-dimensional square grid.
     * On each field of the grid, there can be one {@link FieldEntity}.
     * Each grid has exactly one start position where the player starts.
     */
    public class GameBoard {

        /**
         * The start position of the game board where the player starts.
         */
        private Vector startPostion;
    
        /**
         * The two-dimensional grid of the game board, where each field can contain one {@link FieldEntity}.
         * The first index corresponds to the row (y-coordinate), the second index to the column (x-coordinate).
         * A field is null if it does not contain a {@link FieldEntity}.
         */
        private final FieldEntity[][] board;
    
        /**
         * Constructs a new game board with the given start position and size.
         * The game board is initially empty, i.e. all fields are null.
         * The size of the game board is the number of rows and columns.
         *
         * @param startPosition The start position of the game board where the player starts.
         * @param size The size of the square grid.
         * @throws IllegalArgumentException if the size is less than 1 or the start position is not within the board.
         */
        public GameBoard(Vector startPosition, int size) throws IllegalArgumentException{
    
            if (size < 1) {
                throw new IllegalArgumentException("Size must be at least 1!");
            }
    
            if (startPosition.x() < 0 || startPosition.x() >= size || startPosition.y() < 0 || startPosition.y() >= size) {
                throw new IllegalArgumentException("Start position must be within the board!");
            }
    
            this.startPostion = startPosition;
            this.board = new FieldEntity[size][size];
        }
    
        /**
         * Returns the start position of the game board where the player starts.
         * @return the start position.
        */
        public Vector getStartPosition() {
            return startPostion;
        }
    
        /**
         * Sets the start position of the game board where the player starts.
         * @param startPosition the start position.
        */
        public void setStartPosition(Vector startPosition) {
            this.startPostion = startPosition;
        }
    
    }

    /**
     * Represents an entity that can be placed on a {@link GameBoard}.
     */
    public interface FieldEntity {

        /**
         * Executes this entity's action for the current turn.
         * This method is called once per turn.
        */
        void doAction();
    
        /**
         * Returns the current position of this entity on the game board.
         * @return the current position.
         */
        Vector getPosition();
    
        /**
         * Returns whether this entity is the player.
         * @return true if this entity is the player, false otherwise.
        */
        boolean isPlayer();
    }

    /**
     * A {@link FieldEntity} that represents a Wall on a game board at a given position.
     * Walls do not do anything besides being an immovable obstacle.
     */
    public class Wall implements FieldEntity {
    
        /**
         * The position of this wall on the game board.
         * Walls do not move, so this position is immutable.
         */
        private final Vector position;
    
        /**
         * Creates a new wall at the given position.
         * @param position The position of this wall on the game board.
         */
        public Wall(Vector position) {
            this.position = position;
        }
    
        @Override
        public void doAction() {
            // Walls do not do anything
        }
    
        @Override
        public Vector getPosition() {
            return position;
        }
    
        @Override
        public boolean isPlayer() {
            return false;
        }
    }

    /**
     * Represents an immutable, two-dimensional vector (x, y).
     *
     * @param x The first component of this vector.
     * @param y The second component of this vector.
     */
    public record Vector(int x, int y) {

        /**
         * Calculates the sum of the current vector and the given vector and returns the result as a new vector.
         * The current vector and the given vector are not modified.
         *
         * @param other The vector to add to the current vector.
         * @return A new vector representing the sum of the current vector and the given vector.
         */
        public Vector add(Vector other) {
            return new Vector(x + other.x, y + other.y);
        }

        /**
         * Calculates the Euclidean norm of the current Vector.
         *
         * @return Euclidean norm of the vector (x,y)
         */
        public double euclid2() {
            return Math.sqrt(x * x + y * y);
        }

    }

    /**
     * Represents a Direction in a two-dimensional grid.
     */
    public enum Direction {

        /**
         * The direction up. This direction corresponds to the vector (0, 1).
         */
        UP(new Vector(0, 1)),
    
        /**
         * The direction down. This direction corresponds to the vector (0, -1).
         */
        DOWN(new Vector(0, -1)),
    
        /**
         * The direction left. This direction corresponds to the vector (-1, 0).
         */
        LEFT(new Vector(-1, 0)),
    
        /**
         * The direction right. This direction corresponds to the vector (1, 0).
         */
        RIGHT(new Vector(1, 0));

        /**
         * The vector describing the current Direction.
         */
        private final Vector directionVector;
    
        /**
         * Constructs a new Direction along the given vector.
         * @param directionVector The vector describing the current Direction.
         */
        public Direction(Vector directionVector) {
            this.directionVector = directionVector;
        }
    
        /**
         * Returns a new vector which is the result of shifting the given position by the current direction.
         * @param position The position to shift.
         * @return The position shifted by the current direction.
         */
        public Vector apply(Vector position) {
            return position.add(directionVector);
        }
    }

    ```

* In der [Dokumentation der Java Standardbibliothek] finden Sie etliche Beispiele, wie gute JavaDoc Kommentare aussehen sollten.
* Weiter unten auf dieser Seite finden Sie zusätzlich ein paar Negativbeispiele.

## Aufbau

* Zu Beginn eines JavaDoc Kommentars steht eine allgemeine Beschreibung der Methode, welche auf alle Details der Methode eingeht und beschreibt, was sie bewirkt, wie sie zu benutzten ist und was man dabei beachten muss.
* Danach folgen sogenannte Tags, welche mit einem **@** und dem Namen des Tags beginnen.
* Jeder JavaDoc Kommentar muss dabei, falls notwendig, folgende Tags haben:
    * **@param Parametername description** Beschreibt kurz die Bedeutung des Parameters **Parametername**.
      Für jeden Parameter muss ein solcher Tag vorhanden sein.
    * **@return description** Beschreibt kurz die Bedeutung der Rückgabe der Methode.
      Wenn die Methode keine Rückgabe hat, wird dieser Tag weggelassen.
    * **@throws Exceptionname description** Beschreibt kurz, in welchem Fall die Exception **Exceptionname** geworfen wird.
      Für jede Exception, welche in der throws-Klausel der Methode angegeben wird, muss ein solcher Tag vorhanden sein.
        * Optional können Sie diesen Tag auch für Runtime Exceptions hinzufügen, welche geworfen werden können.

## Verpflichtende Dokumentation

* Ab dem dritten Übungsblatt kann es vorkommen, dass von Ihnen gefordert wird, Ihren selbstgeschriebenen Code zu dokumentieren. Wenn dies der Fall ist, müssen alle von Ihnen deklarierten Klassen, Interfaces, Enums und Methoden (inklusive Konstruktoren) mittels JavaDoc dokumentiert werden.
* Private Methoden und Methoden, welche andere, bereits dokumentierte, Methoden überschreiben, sowie private Attribute und Enumerationselemente müssen **nicht** dokumentiert werden.

## Einige weitere Tags
* **@author name** Gibt den Autor an.
  Kann nur in Klassen, Interface und Enums verwendet werden.
*  **@version version** Gibt die Version an.
  Kann nur in Klassen, Interface und Enums verwendet werden.
*  **@since version** Gibt an, seit wann das Objekt verfügbar ist.
*  **@see reference** Erzeugt eine Referenz auf eine andere Dokumentation.
*  **@deprecated** Gibt an, dass die Methode veraltet ist und nicht verwendet werden sollte.
*  Eine vollständige Liste finden Sie [hier].

## Negativbeispiele

* Anbei finden Sie einige Negativbeispiele, welche zeigen, wie JavaDoc Kommentare **nicht** aussehen sollten.

* !!! Example
    ```java
    /**
     * This is an implementation of a method that calculates the Euclidean norm of a Vector.
     * This is done by first calculating the square of the first and second component of the vector
     * and then adding them together. After that the square root of the sum is calculated and returned.
     * The square root is calculated using the Math.sqrt method.
     *
     * @return Euclidean norm of the vector (x,y), as described above.
     */
    public double euclid2() {
        return Math.sqrt(x*x + y*y);
    }
    ```
    * JavaDoc Kommentare sollten nur kurz und prägnant beschreiben, was eine Methode macht.
      Sie sollten nicht erklären, wie genau die Methode Schritt für Schritt funktioniert, 
      oder aus Sicht einer Aufgabenstellung beschreiben wie die Methode implementiert wurde.

* !!! Example
    ```java
    /** 
     * @param x An int value.
     * @param y An int value.
     */
    public Vector(int x, int y) {
        this.x = x;
        this.y = y;
    }
    ```
    * Es fehlt eine Beschreibung des Konstruktors. Auch wenn der Konstruktor trivial ist, sollte er trotzdem kurz beschrieben werden.
    * Die Parameter werden nicht ausreichend beschrieben. Es sollte kurz erklärt werden, was die Parameter bedeuten und wie sie zu benutzen sind.
      Die Typen der Parameter werden nicht angegeben, da diese aus dem Methodenkopf ersichtlich sind.

* !!! Example
    ```java
    /** 
     * Does something.
     */
    public void doAction();
  
    /**
     * Returns a boolean.
     * @return a boolean.
     */
    public boolean isPlayer();
    ```
    * Es fehlt eine genauere Beschreibung der Methode. Auch wenn Methoden in Interfaces nicht implementiert werden, 
      sollten trotzdem kurz beschrieben werden, was eine Implementierung der Methode tut.

* !!! Example
    ```java
    /** 
     * A class that implements FieldEntity. It implements all methods of FieldEntity.
     */
    public class Wall implements FieldEntity{...}
    ```
    * Es fehlt eine genauere Beschreibung was die Klasse macht und was ein Objekt dieser Klasse repräsentiert.
    * Es ist nicht notwendig explizit zu erwähnen, dass die Klasse ein Interface implementiert und welche Methoden sie implementiert.

[hier]: https://de.wikipedia.org/wiki/Javadoc#%C3%9Cbersicht_der_Javadoc-Tags
[Dokumentation der Java Standardbibliothek]: https://docs.oracle.com/en/java/javase/17/docs/api/java.base/module-summary.html
