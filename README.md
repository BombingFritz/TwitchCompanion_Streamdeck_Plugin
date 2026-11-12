# TwitchCompanion Stream Deck Plugin

Stream-Deck-Plugin für den [Twitch Companion JS server](https://github.com/BombingFritz/Twitch-Companion-JS-server): fertige Aktionen für Server-Funktionen mit Live-Anzeige auf den Tasten. Ein Plugin für alle Module.

> **Schnittstelle und Fahrplan stehen im Server-Repository:** `docs/specs/stream-deck.md`, `docs/FAHRPLAN.md`, ADR 0020. Dieses Repository führt keinen eigenen Fahrplan.

## Geplante Aktionen (0.1)
| Aktion | Server-Aufruf |
|---|---|
| Topics weiter | `POST /api/topics/next` |
| Topics zurück | `POST /api/topics/back` |
| Topics ein/aus | `POST /api/topics/toggle` |
| Clip-Moment | `POST /api/clip/mark` |

## Stand
Noch kein Code. Das Gerüst entsteht mit der Elgato-CLI (`npm install -g @elgato/cli`, `streamdeck create`), sobald die Server-Endpoints stehen (Fahrplan Schritt 8).

## Bis dahin
Die Endpoints lassen sich mit einem fertigen HTTP-Plugin (z. B. „API Request“) belegen: Methode POST, Header `Content-Type: application/json`, Body `{}`.

## Voraussetzungen und Serverkompatibilität
- Stream-Deck-Software; Mindestversion folgt mit dem Gerüst [UNGEKLÄRT].
- Twitch Companion JS server mit den Endpoints aus `docs/specs/stream-deck.md`. Erste kompatible Server-Version: [noch nicht veröffentlicht].

## Daten, Speicherung, Netzwerk
- Netzwerk: nur Aufrufe an den eigenen Server unter `localhost`. Keine Verbindungen ins Internet, keine Telemetrie, keine KI- oder Cloud-Dienste.
- Speicherung: nur die Plugin-Einstellungen in der Stream-Deck-Software (Server-Adresse).
- Berechtigungen: keine Twitch-Scopes, kein Token.

## Fremde Bestandteile
Geplant: Elgato Stream Deck SDK (`@elgato/streamdeck`, npm). Lizenz und Hinweise werden mit dem Gerüst geprüft und hier eingetragen.

## Lizenz
[MIT](LICENSE). Das Plugin ist ein eigenständiges Modul; der Server steht unter einer eigenen Lizenz (siehe Server-Repository).
