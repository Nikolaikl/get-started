# Branching Strategien für effektive Zusammenarbeit

Eine klare Branching-Strategie ist essentiell für erfolgreiche Teamarbeit, besonders während des Hackathons!

## Grundlegende Konzepte

- **Main Branch**: Stabile Version des Projekts
- **Feature Branches**: Entwicklung neuer Funktionen
- **Pull Requests**: Code-Review und Integration

## Workflow für den Hackathon

1. **Feature Branch erstellen**
   ```bash
   git checkout -b feature/mein-feature
   ```

2. **Regelmäßig committen**
   ```bash
   git add .
   git commit -m "Beschreibung der Änderungen"
   ```

3. **Mit main Branch synchronisieren**
   ```bash
   git checkout main
   git pull origin main
   git checkout feature/mein-feature
   git merge main
   ```

4. **Pull Request erstellen**
   - Gehen Sie zu GitHub
   - Erstellen Sie einen neuen Pull Request
   - Beschreiben Sie Ihre Änderungen
   - Weisen Sie Reviewer zu

5. **Code Review**
   - Diskutieren Sie Änderungen
   - Beheben Sie Konflikte
   - Verbessern Sie den Code basierend auf Feedback

6. **Merge in main**
   - Nach erfolgreichem Review
   - Löschen Sie den Feature Branch

## Best Practices

- Halten Sie Branches klein und fokussiert
- Benennen Sie Branches klar und beschreibend
- Committen Sie häufig mit aussagekräftigen Nachrichten
- Lösen Sie Konflikte sofort
- Nutzen Sie Pull Requests für jede Änderung
- Führen Sie regelmäßig Code Reviews durch

## Branch-Namenskonventionen

- feature/mein-neues-feature
- bugfix/behebung-des-problems
- hotfix/kritischer-fehler
- experiment/neue-idee

## Tools

- lazygit cli tool
- github plugin in VsCode
