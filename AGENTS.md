# AGENTS.md – Regeln für KI-Assistenten

## Zusammenarbeit mit dem Server-Repository
- Im Server-Repository `BombingFritz/Twitch-Companion-JS-server` nur **lesen** und **Issues anlegen oder ergänzen** (Vorlage „Serveranforderung“). Keine Branches, Commits, Pull Requests, Kommentare in fremden PRs und keine Änderungen an Code oder Doku (Specs, ADRs, Fahrplan, `OFFEN.md`), auch nicht als Vorschlag zum Selbermachen (Nutzer, 26.11.2026).
- Grundlage: Abschnitt „Zuständigkeit“ und „Issues von Verbrauchern“ in der `AGENTS.md` des Servers. Diese Datei vor jeder Arbeit lesen, nicht nur `CLAUDE.md` (die verweist nur darauf).
- Vor einem neuen Issue die offenen Server-Issues prüfen und vorhandene ergänzen statt doppeln. Fehlt der Zugriff, das sagen und den Entwurf liefern.
- Die Server-Session baut, präzisiert die Spec und meldet sich per Issue im Plugin-Repository, wenn etwas fertig ist. API-Vorschläge im Issue sind erst nach ihrer Spec-Änderung vereinbart.
- Server-Issues verweisen auf das zugehörige Feature-Issue in diesem Repository.

## Vor jeder Änderung
- Schnittstelle und Fahrplan stehen im Server-Repository `BombingFritz/Twitch-Companion-JS-server`: `docs/specs/stream-deck.md`, `docs/FAHRPLAN.md`, ADR 0020. Dort zuerst lesen (dazu dessen `AGENTS.md`) und den aktuellen Stand auf GitHub prüfen.
- Neue Aktionen brauchen zuerst einen Endpoint in der Spec des Server-Repositories; fehlt er, ein Server-Issue anlegen (siehe oben).
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
