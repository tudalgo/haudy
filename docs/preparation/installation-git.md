# Installieren von Git

!!! info "Information"
    Git ist ein Versionsverwaltungssystem, das wir für die Veröffentlichung Übungsvorlagen auf [GitHub] verwenden.
    Auch wenn Sie Git nicht verwenden müssen, empfehlen wir Ihnen, da Sie so die Vorlagen einfacher herunterladen und aktualisieren können und das Arbeiten mit Git beim Programmieren früher oder später unumgänglich ist.
    
=== "Windows"
    === "Scoop"
        1. Falls noch nicht geschehen, installieren Sie [Scoop].
        2. Führen Sie folgende Befehle in einem [Terminal] aus, um Git zu installieren:
            ```
            scoop install git
            ```
    === "Manuell"
        1. Laden Sie sich [Git] herunter, indem Sie rechts auf **"Download for Windows"** drücken.
        2. Führen Sie den soeben heruntergeladenen Installer aus.
        3. Drücken Sie so lange auf **"Next"**, bis der Installationsprozess beginnt. Sie können die Standardeinstellungen des Installers übernehmen und müssen nichts weiter auswählen.
        4. Drücken Sie auf **"Finish** um den Installationsprozess abzuschließen.
        5. Sie können nun mit dem Befehl **"git --version"** in einer Konsole überprüfen, ob Git erfolgreich installiert wurde.
           * Sie können ein Terminal öffnen, indem Sie in der Windowssuche (Win+ S) **"cmd"** eingeben.

=== "macOS"
    === "Homebrew"
        1. Falls noch nicht geschehen, installieren Sie [Homebrew].
        2. Führen Sie in einem [Terminal] folgenden Befehl aus, um Git zu installieren.
            ```
            brew install git
            ```

=== "Linux"
    === "Debian/Ubuntu"
        1. Installieren Sie Git mit dem folgenden Befehl:
            ```
            sudo apt install git
            ```
    === "Fedora"
        1. Installieren Sie Git mit dem folgenden Befehl:
            ```
            sudo dnf install git
            ```
    === "Arch Based Linux"
        1. Installieren Sie Git mit dem folgenden Befehl:
            ```
            sudo pacman -S git
            ```

* Sie können nun mit dem Befehl **"git --version"** in einem [Terminal] überprüfen, ob Git erfolgreich installiert wurde.
    

[GitHub]: https://github.com/FOP-2526
[Git]: https://git-scm.com/download
[Terminal]: https://wiki.tudalgo.org/preparation/terminal/
[Homebrew]: https://wiki.tudalgo.org/preparation/packagemanager/
[Scoop]: https://wiki.tudalgo.org/preparation/packagemanager/
