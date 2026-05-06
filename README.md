# 🛠️ AI-Toolkit: The Agent Orchestrator

Dieses Repository ist die zentrale Schaltzentrale für deine KI-Workflows. Es dient als **Master-Registry** für Agenten-Definitionen, Skill-Sets und Hooks, die modular in verschiedene lokale Projekte (Claude Code, GitHub Copilot, etc.) injiziert werden können.

---

## 🏗️ Projektstruktur

Das Toolkit ist nach Providern und Anwendungsbereichen getrennt. Jedes Modul folgt einem konsistenten Aufbau, um die Portabilität zu gewährleisten.

    ai-toolkit/
    ├── general-ai-toolkit/          # Globale Standards & Basis-Skills
    │   ├── claude/
    │   │   ├── install-toolkit.py   # Das Installations- & Sync-Skript
    │   │   └── .claude/             # Definitionen (Source)
    │   │       ├── Agents/          # Rollendefinitionen (z.B. Architect.md)
    │   │       ├── Skills/          # Spezifische Fähigkeiten (z.B. SQL-Expert.md)
    │   │       └── Hooks/           # Automatisierungen & Standards
    │   └── copilot/
    │       └── ...
    └── exampleProject-ai-toolkit/   # Projektspezifische Erweiterungen (Overrides)

---

## 🚀 Workflow: So nutzt du das Toolkit

Das Ziel ist es, deine "Best Practice" Prompts an einem Ort zu pflegen und sie per Skript in deine aktiven Projekte zu "provisionieren".

### 1. Installation im Zielprojekt
Um die Skills in deinem aktuellen Arbeitsprojekt verfügbar zu machen, führst du den Installer aus dem Toolkit-Repo im Kontext deines Zielprojekts aus:

    # Navigiere in dein eigentliches Arbeitsprojekt
    cd ~/projects/mein-neues-projekt
    
    # Führe den Installer aus dem Toolkit aus
    python ~/path/to/ai-toolkit/general-ai-toolkit/claude/install-toolkit.py

### 2. Was der Installer tut
Die `install-toolkit.py` automatisiert das Setup deiner `.claudecode/config`:
*   **Symlinking/Copy:** Sie spiegelt die MD-Dateien aus diesem Repo in den lokalen `.claudecode/config` Ordner deines Projekts.
*   **Namespacing:** Dateien werden beim Transfer markiert (z.B. `General_Skill_Refactoring.md`), um die Herkunft klar zu kennzeichnen.
*   **Persistenz:** Änderungen im Toolkit werden (bei Symlinks) sofort in allen verknüpften Projekten übernommen.

---

## 🧠 Komponenten-Definitionen

### 🤖 Agents (`/Agents`)
Hier liegen die "System-Prompts" für verschiedene Rollen. Sie definieren, wie die KI sich verhält (z.B. Senior Fullstack Dev, DevOps Engineer, Security Auditor).

### ⚡ Skills (`/Skills`)
Modulare Fähigkeiten. Ein Skill ist eine spezialisierte Anleitung für eine bestimmte Aufgabe, z.B. "Schreibe Unit-Tests nach dem AAA-Muster" oder "Optimiere SQL-Abfragen".

### ⚓ Hooks (`/Hooks`)
Hooks sind Verhaltensregeln, die bei jedem Prompt greifen sollen. Sie erzwingen Coding-Standards, Dokumentationspflichten oder spezifische Antwortformate.

---

## 🛠️ Anpassung & Erweiterung

Wenn du einen neuen Skill erstellst:
1. Erstelle eine neue `.md`-Datei im passenden Unterordner.
2. Nutze klare Markdown-Strukturen (`#`, `##`, `-`).
3. Führe den Installer in deinen Projekten erneut aus, um den neuen Skill zu registrieren.

---

## 📝 Best Practices
*   **Modularität:** Eine Datei pro Skill. Vermische keine Rollen (z.B. trenne `CSS-Expert` von `Backend-Dev`).
*   **Versionskontrolle:** Da dies ein Git-Repo ist, kannst du deine Prompt-Iterationen perfekt tracken.
*   **Keine Secrets:** Speichere niemals API-Keys oder Zugangsdaten in diesen MD-Dateien!

---
*Erstellt mit dem Fokus auf maximale Effizienz in der lokalen KI-Interaktion.*
