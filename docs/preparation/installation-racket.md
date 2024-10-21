# Installieren von DrRacket

=== "Windows"

    === "Scoop"

          1. Falls noch nicht geschehen, installieren Sie [Scoop].
          2. Führen Sie folgenden Befehl in einem [Terminal] aus, um Racket zu installieren:
              ```
              scoop install racket
              ```

    === "Manuell"

          1. Laden Sie [hier] DrRacket herunter. Achten Sie darauf, dass Windows als Betriebssystem ausgewählt ist.
          2. Führen Sie den heruntergeladenen Installer aus und drücken Sie auf **"Next"**, bzw. **"Install"**, bis der Installationsprozess abgeschlossen ist und am Ende auf **"Finish"**.

=== "macOS"

    === "Homebrew"

          1. Falls noch nicht geschehen, installieren Sie [Homebrew].
          2. Führen Sie in einem [Terminal] folgenden Befehl aus, um Racket zu installieren.
            ```
            brew install --cask racket
            ```
            
    === "Manuell"
         1. Laden Sie [hier] DrRacket herunter. Achten Sie darauf, dass Mac OS als Betriebssystem ausgewählt ist.
         2. Öffnen Sie die heruntergeladenen .dmg Datei.
         3. Kopieren Sie die Racket Installation in den Applications Ordner.

=== "Linux"
    === "Manuell"
         1. Laden Sie [hier] DrRacket herunter. Achten Sie darauf, dass Linux als Betriebssystem ausgewählt ist.
           * Alternativ können Sie es auch mit dem folgenden Befehl herunterladen:
           ```
           wget https://mirror.racket-lang.org/installers/8.6/racket-8.6-x86_64-linux.sh
           ```
         2. Stellen Sie mit
         ```
         chmod +x racket-8.6-x86_64-linux.sh
         ```
         sicher, dass der Installer ausführbar ist und führen Sie diesen dann mit
         ```
         sudo ./racket-8.6-x86_64-linux.sh
         ```
         aus.
         4. Beantworten Sie die Fragen, die Ihnen im Terminal gestellt werden. Standardmäßig können diese mit **"no"**, **"1"** und **"/usr/local"** beantworten. 

    === "Arch Based Linux"

         1. Installieren Sie Racket (als Root).
            ```
            pacman -S racket --needed
            ```

## DrRacket einrichten

* Öffnen Sie nun DrRacket und gehen Sie auf oben auf **"Language"** -> **"Choose Language"** und wählen Sie unter **"Teaching Languages"** **"Advanced Student"** aus. Bestätigen Sie danach die Auswahl, indem Sie auf **"OK"** drücken.
* Nun können Sie Racket Programme ausführen, indem Sie rechts oben auf **"Run"** drücken.

## Installation überprüfen

* Zum Überprüfen der Installation von Racket können Sie folgenden Befehl in einem [Terminal] ausführen:
```
racket --version
```

* Wenn die Ausgabe in etwa so aussieht, ist die Installation erfolgreich.
    ```
    Welcome to Racket v8.14 [cs].
    ```
## Windows - Umgebungsvariablen einstellen

* Falls bei der [Überprüfung der Installation] eine Fehlermeldung wie
```
Der Befehl "racket" ist entweder falsch geschrieben
oder konnte nicht gefunden werden.
```
angezeigt wird, überprüfen Sie wie folgt, ob die Umgebungsvariablen korrekt gesetzt sind.:
    1. Geben Sie in die Windowssuche (Win + S) **"Systemumgebungsvariablen bearbeiten"** ein und öffnen Sie das Fenster.
    2. Drücken Sie rechts unten auf **"Umgebungsvariablen"**.
    3. Wählen Sie die Variable **"Path"** aus und drücken Sie auf **"Bearbeiten..."**.
    4. In der nun angezeigten Liste sollte der Eintrag zum Installationspfad von Racket enthalten sein, der wie folgt aussehen könnte:
    ```
    C:\Program Files\Racket
    ```
    Falls nicht, fügen Sie diesen rechts oben mit dem Knopf **"Neu"** hinzu.
    5. Schließen Sie mit **"OK"** alle Fenster und öffnen Sie ein neues Terminal. Es sollte nun die Hilfeausgabe von raco angezeigt werden.

[hier]: https://download.racket-lang.org/
[Terminal]: https://wiki.tudalgo.org/preparation/terminal/
[Überprüfung der Installation]: #installation-uberprufen
[Homebrew]: https://wiki.tudalgo.org/preparation/packagemanager/
[Scoop]: https://wiki.tudalgo.org/preparation/packagemanager/
