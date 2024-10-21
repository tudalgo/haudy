# Installation für das Recap
Stellen Sie sicher, dass Sie bereits [Java] und [Racket] installiert haben.

## Installieren von Anaconda

=== "Windows"
    === "Scoop"
        1. Falls noch nicht geschehen, installieren Sie [Scoop].
        2. Führen Sie folgende Befehle in einem [Terminal] aus, um Anaconda zu installieren:
            ```
            scoop bucket add extras
            ```
            und
            ```
            scoop install extras/anaconda3
            ```

    === "Manuell"
        1. Laden Sie [hier] Anaconda herunter. Achten Sie darauf, dass Windows als Betriebssystem ausgewählt ist.
        2. Führen Sie den heruntergeladenen Installer aus und drücken Sie auf **"Next"**, bzw. **"Install"**, bis der Installationsprozess abgeschlossen ist und am Ende auf **"Finish"**.

=== "macOS"

    === "Homebrew"
        1. Falls noch nicht geschehen, installieren Sie [Homebrew].
        2. Führen Sie in einem [Terminal] folgenden Befehl aus, um Racket zu installieren.
            ```
            brew install --cask anaconda
            ```
            
    === "Manuell"
        1. Laden Sie [hier] Anaconda als .pkg Datei herunter. Achten Sie darauf, dass Mac OS als Betriebssystem ausgewählt ist.
        2. Öffnen Sie die heruntergeladene .pkg Datei, führen den Installer aus und drücken Sie auf **"Continue"**, bzw. **"Install"**, bis der Installationsprozess abgeschlossen ist und am Ende auf **"Finish"**.

=== "Linux"
    === "Debian/Ubuntu"
        1. Führen Sie in einem [Terminal] folgenden Befehl aus, um die Voraussetzungen zu installieren.
        ```
        sudo apt install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
        ```

    === "Fedora"
        1. Führen Sie in einem [Terminal] folgenden Befehl aus, um die Voraussetzungen zu installieren.
        ```
        sudo dnf install libXcomposite libXcursor libXi libXtst libXrandr alsa-lib mesa-libEGL libXdamage mesa-libGL libXScrnSaver
        ```

    === "Arch Based Linux"
        1. Führen Sie in einem [Terminal] folgenden Befehl aus, um die Voraussetzungen zu installieren.
        ```
        pacman -Sy libxau libxi libxss libxtst libxcursor libxcomposite libxdamage libxfixes libxrandr libxrender mesa-libgl alsa-lib libglvnd
        ```

    1. Laden Sie [hier] Anaconda herunter. Achten Sie darauf, dass Linux als Betriebssystem ausgewählt ist.
        * Alternativ können Sie es auch mit dem folgenden Befehl herunterladen:
        ```
        curl -O https://repo.anaconda.com/archive/Anaconda3-<INSTALLER_VERSION>-Linux-x86_64.sh
        ```
    2. Führen Sie in einem [Terminal] folgenden Befehl aus, um den Installationsprozess zu starten.
    ```
    bash ~/Downloads/Anaconda3-<INSTALLER_VERSION>-Linux-x86_64.sh
    ```
    3. Akzeptieren Sie die Lizenzvereibarung für Anaconda, indem Sie **"Enter"** drücken und zum Scrollen gedrückt halten und am Ende **"Yes"** eingeben.
    4. Drücken Sie **"Enter"**, um den Standardinstallationspfad zu akzeptieren oder geben Sie einen alternativen vollständigen Installationspfad an.
    5. Geben Sie **"Yes"** ein, um die Anaconda Distribution zu initialisieren.
    6. Schließen Sie nach Abschluss der Installation das aktuelle Terminal und öffnen Sie ein neues.
    7. Geben Sie folgenden Befehl ein, um Ihre Installation zu verifizieren und als Ausgabe alle installieren Packages zu erhalten.
    ```
    conda list
    ```
    
## Installation Java Kernel
=== "Windows"
    === "Manuell"
        1. Laden Sie sich den Kernel [iJava] herunter, indem Sie unten auf das Zip-Archiv **"ijava-1.3.0.zip"** drücken.
        2. Entpacken Sie das heruntergeladene Zip-Archiv.
        3. Geben Sie in die Windowssuche (Win + S) **"Anaconda Prompt"** ein und öffnen Sie das Fenster.
        4. Navigieren Sie zum Verzeichnis, wo sich die entpackte Zip-Datei befindet z.B.:
        ```
        cd C:\Users\DeinUsername\Dowloads\ijava-1.3.0
        ```
        Am besten navigieren Sie über den Windows-Explorer in das Verzeichnis und kopieren den Pfad oben aus der Leiste.
        5. Installieren Sie den Java Kernel mittels:
        ```
        python install.py --user
        ```
=== "macOS"
    === "Manuell"
        1. Laden Sie sich den Kernel [iJava] herunter, indem Sie unten auf das Zip-Archiv **"ijava-1.3.0.zip"** drücken.
        2. Entpacken Sie das heruntergeladene Zip-Archiv.
        3. Führen Sie in einem [Terminal] folgenden Befehl aus, um sicherzustellen, dass Sie sich in einer Anaconda Umgebung befinden.
        ```
        conda activate
        ```
        4. Navigieren Sie zum Verzeichnis, wo sie die entpackete Zip-Datei befindet.
        5. Installieren Sie den Java Kernel mittles:
        ```
        python install.py --user
        ```

=== "Linux"
    === "Manuell"
        1. Laden Sie sich den Kernel [iJava] herunter, indem Sie unten auf das Zip-Archiv **"ijava-1.3.0.zip"** drücken.
        2. Entpacken Sie das heruntergeladene Zip-Archiv.
        3. Führen Sie in einem [Terminal] folgenden Befehl aus, um sicherzustellen, dass Sie sich in einer Anaconda Umgebung befinden.
        ```
        conda activate
        ```
        4. Navigieren Sie zum Verzeichnis, wo sie die entpackete Zip-Datei befindet.
        5. Installieren Sie den Java Kernel mittles:
        ```
        python install.py --user
        ```

## Installation Racket Kernel
=== "Windows"
    === "Manuell"
        1. Geben Sie in die Windowssuche (Win + S) **"Anaconda Prompt"** ein und öffnen Sie das Fenster.
        2. Führen Sie folgenden Befehl aus, um iRacket zu installieren.
        ```
        raco pkg install iracket
        ```
        3. Beantworten Sie die Frage **"Would you like to install these dependencies?"** mit **"Y"**.
        4. Führen Sie folgenden Befehl aus, um den iRacket Kernel bei Jupyter zu registrieren.
        ```
        raco iracket install
        ```

=== "macOS"
    === "Manuell"
        1. Führen Sie in einem [Terminal] folgenden Befehl aus, um sicherzustellen, dass Sie sich in einer Anaconda Umgebung befinden.
        ```
        conda activate
        ```
        2. Führen Sie folgenden Befehl aus, um ZeroMQ zu installieren.
        ```
        brew install zmq
        ```
        3. Führen Sie folgenden Befehl aus, um iRacket zu installieren.
        ```
        raco pkg install iracket
        ```
        4. Beantworten Sie die Frage **"Would you like to install these dependencies?"** mit **"Y"**.
        5. Führen Sie folgenden Befehl aus, um den iRacket Kernel bei Jupyter zu registrieren.
        ```
        raco iracket install
        ```

=== "Linux"
    === "Debian/Ubuntu"
        1. Führen Sie in einem [Terminal] folgenden Befehl aus, um sicherzustellen, dass Sie sich in einer Anaconda Umgebung befinden.
        ```
        conda activate
        ```
        2. Führen Sie folgenden Befehl aus, um ZeroMQ zu installieren.
        ```
        sudo apt install libzmq5
        ```
        3. Führen Sie folgenden Befehl aus, um iRacket zu installieren.
        ```
        raco pkg install iracket
        ```
        4. Beantworten Sie die Frage **"Would you like to install these dependencies?"** mit **"Y"**.
        5. Führen Sie folgenden Befehl aus, um den iRacket Kernel bei Jupyter zu registrieren.
        ```
        raco iracket install
        ```
    === "Fedora"
        === "Debian/Ubuntu"
        1. Führen Sie in einem [Terminal] folgenden Befehl aus, um sicherzustellen, dass Sie sich in einer Anaconda Umgebung befinden.
        ```
        conda activate
        ```
        2. Führen Sie folgenden Befehl aus, um ZeroMQ zu installieren.
        ```
        sudo dnf install zeromq
        ```
        3. Führen Sie folgenden Befehl aus, um iRacket zu installieren.
        ```
        raco pkg install iracket
        ```
        4. Beantworten Sie die Frage **"Would you like to install these dependencies?"** mit **"Y"**.
        5. Führen Sie folgenden Befehl aus, um den iRacket Kernel bei Jupyter zu registrieren.
        ```
        raco iracket install
        ```

[ijava]: https://github.com/SpencerPark/IJava/releases/tag/v1.3.0/
[hier]: https://www.anaconda.com/download/success/
[Terminal]: https://wiki.tudalgo.org/preparation/terminal/
[Installations Anleitung]: https://docs.anaconda.com/anaconda/install/linux/
[Java]: installation-java.md
[Racket]: installation-racket.md
[Homebrew]: https://wiki.tudalgo.org/preparation/packagemanager/
[Scoop]: https://wiki.tudalgo.org/preparation/packagemanager/
