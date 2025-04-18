# Sicherheitsbest Practices für GitHub

Sicherheit ist entscheidend bei der Arbeit mit sensiblen Daten und Code. Hier sind wichtige Maßnahmen:

## Account-Sicherheit

1. **Zwei-Faktor-Authentifizierung (2FA) aktivieren**
   - Gehen Sie zu GitHub Account Settings
   - Wählen Sie "Security"
   - Aktivieren Sie 2FA

2. **Starke Passwörter verwenden**
   - Mindestens 12 Zeichen
   - Kombination aus Buchstaben, Zahlen und Sonderzeichen
   - Keine Wiederverwendung von Passwörtern

3. **SSH-Schlüssel verwenden**
   - Erstellen Sie einen neuen SSH-Schlüssel:
     ```bash
     ssh-keygen -t ed25519 -C "your_email@example.com"
     ```
   - Fügen Sie den öffentlichen Schlüssel zu GitHub hinzu

## Repository-Sicherheit

1. **Zugriffsrechte beschränken**
   - Nur notwendige Personen Zugriff gewähren
   - Teams mit klaren Rollen erstellen

2. **Sicherheitswarnungen aktivieren**
   - Dependabot für Sicherheitsupdates aktivieren
   - Code-Scanning aktivieren

3. **Sensible Daten schützen**
   - Niemals Passwörter oder API-Keys im Code speichern
   - GitHub Secrets für sensible Daten verwenden
   - .gitignore Datei korrekt konfigurieren

## Codespaces Sicherheit

1. **Automatische Sperrung konfigurieren**
   - Setzen Sie Timeout für Inaktivität
   - Beenden Sie nicht genutzte Codespaces

2. **Netzwerksicherheit**
   - Nutzen Sie Port-Forwarding mit Vorsicht
   - Beschränken Sie den Zugriff auf Ports

3. **Umgebungsvariablen schützen**
   - Nutzen Sie GitHub Secrets
   - Keine sensiblen Daten in Klartext speichern

## Signed Commits

1. **GPG-Schlüssel erstellen**
   ```bash
   gpg --full-generate-key
   ```
   - RSA-Schlüsseltyp wählen
   - 4096 Bit Schlüssellänge
   - Gültigkeitsdauer festlegen

2. **Schlüssel zu GitHub hinzufügen**
   - Öffentlichen Schlüssel anzeigen:
     ```bash
     gpg --armor --export YOUR_KEY_ID
     ```
   - In GitHub unter Settings -> SSH and GPG keys einfügen

3. **Git für Signierung konfigurieren**
   ```bash
   git config --global user.signingkey YOUR_KEY_ID
   git config --global commit.gpgsign true
   ```

4. **Commits signieren**
   - Normaler Commit:
     ```bash
     git commit -S -m "Your commit message"
     ```
   - Alle zukünftigen Commits automatisch signieren:
     ```bash
     git config --global commit.gpgsign true
     ```

5. **Signatur überprüfen**
   ```bash
   git log --show-signature
   ```

## Allgemeine Best Practices

- Regelmäßige Sicherheitsaudits durchführen
- Sicherheitsupdates sofort installieren
- Sicherheitsrichtlinien dokumentieren
- Sicherheitsschulungen für alle Teammitglieder
- Sicherheitsvorfälle sofort melden
