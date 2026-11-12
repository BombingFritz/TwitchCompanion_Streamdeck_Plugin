# AGENTS.md – Regeln für KI-Assistenten

## Vor jeder Änderung
- Schnittstelle und Fahrplan stehen im Server-Repository `BombingFritz/Twitch-Companion-JS-server`: `docs/specs/stream-deck.md`, `docs/FAHRPLAN.md`, ADR 0020. Dort zuerst lesen und den aktuellen Stand auf GitHub prüfen.
- Neue Aktionen brauchen zuerst einen Endpoint in der Spec des Server-Repositories.
- SDK-Fragen gegen die aktuelle Elgato-Doku und das npm-Paket `@elgato/streamdeck` prüfen, nicht aus dem Gedächtnis.

## Konventionen
- Ein Plugin für alle Server-Funktionen; eine Aktion je Server-Aufruf.
- Nur Server-Aufrufe über `localhost`; keine Tokens, Secrets oder Twitch-Aufrufe im Plugin.
- Keine Licht- oder OBS-Logik im Plugin.
- Rückmeldung auf der Taste: `showOk` bei Erfolg, `showAlert` bei Fehler; ohne Server einen erkennbaren Fehlerzustand.
- Server-Adresse als globale Einstellung, Standard `http://localhost:3000`.

## Lizenz
- MIT (eigenständiges Modul, Projektvorgabe „Lizenz- und Entwicklungskontext“ vom 12.11.2026). Keinen Servercode hierher kopieren; nur die dokumentierte Schnittstelle nutzen.
- Lizenzen der Abhängigkeiten (SDK, Build-Werkzeuge) prüfen und im README unter „Fremde Bestandteile“ führen.
- Neue Datenflüsse im README unter „Daten, Speicherung, Netzwerk“ nennen.

## Pflicht-Checks
- Build und `streamdeck validate` ohne Fehler.
- Jede Aktion mit laufendem und ohne laufenden Server prüfen, auch innerhalb einer Multi-Aktion.
- `CHANGELOG.md` mit jeder Version; Versionen über Git-Tags (`vX.Y.Z`).
