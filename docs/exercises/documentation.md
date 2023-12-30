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
     * Represents a immutable, two-dimensional vector (x, y).
     */
    public class Vector {
    
        /**
         * The first component of this vector.
         */
        private final float x;
    
        /**
         * The second component of this vector.
         */
        private final float y;
    
        /**
         * Constructs a new vector with the given components.
         *
         * @param x The first component of the created vector.
         * @param y The second component of the created vector.
         */
        public Vector(float x, float y) {
            this.x = x;
            this.y = y;
        }
    
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
            return Math.sqrt(x*x + y*y);
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
     * @param x A float value.
     * @param y A float value.
     */
    public Vector(float x, float y) {
        this.x = x;
        this.y = y;
    }
    ```
    * Es fehlt eine Beschreibung des Konstruktors. Auch wenn der Konstruktor trivial ist, sollte er trotzdem kurz beschrieben werden.
    * Die Parameter werden nicht ausreichend beschrieben. Es sollte kurz erklärt werden, was die Parameter bedeuten und wie sie zu benutzen sind.
      Die Typen der Parameter werden nicht angegeben, da diese aus dem Methodenkopf ersichtlich sind.

[hier]: https://de.wikipedia.org/wiki/Javadoc#%C3%9Cbersicht_der_Javadoc-Tags
[Dokumentation der Java Standardbibliothek]: https://docs.oracle.com/en/java/javase/17/docs/api/java.base/module-summary.html
