# Setup-Skripte für Projekte

Einrichtungsskripte automatisieren die Installation aller benötigten Tools und Abhängigkeiten für ein Projekt.

## Grundstruktur eines Setup-Skripts

```bash
#!/bin/bash

# Fehlerbehandlung
set -euo pipefail

# Aktualisieren der Paketquellen
echo "Aktualisiere Paketquellen..."
sudo apt-get update

# Installiere Basis-Tools
echo "Installiere Basis-Tools..."
sudo apt-get install -y \
    build-essential \
    git \
    curl \
    wget

# Projekt-spezifische Abhängigkeiten
echo "Installiere Projekt-Abhängigkeiten..."
sudo apt-get install -y \
    python3-pip \
    nodejs \
    npm

# Python-Pakete installieren
echo "Installiere Python-Pakete..."
pip3 install -r requirements.txt

# Node.js-Pakete installieren
echo "Installiere Node.js-Pakete..."
npm install

# Berechtigungen setzen
echo "Setze Dateiberechtigungen..."
chmod +x scripts/*.sh

echo "Setup abgeschlossen!"
```

## Best Practices für Setup-Skripte

1. **Idempotenz**: Das Skript sollte mehrfach ausführbar sein
2. **Fehlerbehandlung**: Bei Fehlern sollte das Skript abbrechen
3. **Fortschrittsanzeige**: Klare Statusmeldungen ausgeben
4. **Umgebungsvariablen**: Sensible Daten auslagern
5. **Plattformunabhängigkeit**: Unterschiede zwischen Betriebssystemen berücksichtigen

## Beispiel für ein erweitertes Skript

```bash
#!/bin/bash

# Konfiguration
INSTALL_DIR="/opt/myproject"
LOG_FILE="/var/log/myproject_setup.log"

# Logging initialisieren
exec > >(tee -a "$LOG_FILE") 2>&1

# Funktion für Fehlerbehandlung
handle_error() {
    echo "Fehler aufgetreten in Zeile $1"
    exit 1
}

trap 'handle_error $LINENO' ERR

# Verzeichnis erstellen
echo "Erstelle Installationsverzeichnis..."
sudo mkdir -p "$INSTALL_DIR"
sudo chown $USER:$USER "$INSTALL_DIR"

# Repository klonen
echo "Klone Projekt-Repository..."
git clone https://github.com/mein/projekt.git "$INSTALL_DIR"
cd "$INSTALL_DIR"

# Abhängigkeiten installieren
echo "Installiere Abhängigkeiten..."
./install_dependencies.sh

# Konfigurationsdateien erstellen
echo "Erstelle Konfigurationsdateien..."
cp .env.example .env

echo "Installation erfolgreich abgeschlossen!"
```

## Tipps für den Hackathon

- Erstellen Sie separate Skripte für:
  - Basis-Setup (setup.sh)
  - Abhängigkeiten (install_dependencies.sh)
  - Tests (run_tests.sh)
  - Deployment (deploy.sh)
- Dokumentieren Sie die Skripte im README.md
- Testen Sie die Skripte in einer frischen Umgebung
- Nutzen Sie Docker für komplexe Setups
- Implementieren Sie eine --help Option

## Sicherheitshinweise

- Niemals Passwörter im Skript speichern
- Verwenden Sie .env Dateien für sensible Daten
- Überprüfen Sie externe Skripte vor der Ausführung
- Setzen Sie angemessene Dateiberechtigungen
- Validieren Sie Benutzereingaben
