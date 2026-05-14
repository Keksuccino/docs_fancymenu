---
title: Kommunikation mit Remote-Servern
description: >-
  Senden und empfangen Sie benutzerdefinierte Textdaten zwischen
  FancyMenu-Clients und externen Servern.
---

# Kommunikation mit Remote-Servern

Das System „Kommunikation mit Remote-Servern“ ermöglicht FancyMenu-Clients die Kommunikation mit externen Servern über WebSocket-Verbindungen.

Alle Daten sind textbasiert:

- Klartext wird unterstützt
- JSON wird unterstützt (als normaler Text)

Jede Server-URL erhält zur Laufzeit eine zwischengespeicherte **Request-ID**.
FancyMenu verwendet diese ID, um die Verbindung zu verfolgen und sie in Listener-Variablen bereitzustellen.

# Schnellstart

1. Aktion **Mit Remote-Server verbinden** hinzufügen (optional, aber nützlich zum frühzeitigen Öffnen)
2. Aktion **Daten an Remote-Server senden** mit derselben URL hinzufügen
3. Listener **Bei Empfang von Remote-Server-Daten** hinzufügen, um auf Antworten zu reagieren
4. **Bei Remote-Server verbunden** / **Bei Remote-Server-Verbindung geschlossen** für Logik zum Verbindungsstatus verwenden
5. Verbindungen bei Bedarf mit Schließen-Aktionen schließen

# Aktionen

## Mit Remote-Server verbinden

Initialisiert eine Remote-Server-Verbindung, ohne Nutzlastdaten zu senden.

Eingabe:

- Remote-Server-URL

## Daten an Remote-Server senden

Stellt eine Verbindung her (oder verwendet eine vorhandene Verbindung erneut) und sendet Textdaten.

Eingaben:

1. Remote-Server-URL
2. Daten

## Remote-Server-Verbindung schließen

Schließt eine Verbindung anhand der Request-ID.

Eingabe:

- Verbindungs-Request-ID

## Alle Remote-Server-Verbindungen schließen

Schließt alle derzeit aktiven Remote-Server-Verbindungen.

# Listener

## Bei Remote-Server verbunden

Wird ausgelöst, wenn eine Remote-Server-Verbindung initialisiert wird.

Variablen:

- `$$request_id`
- `$$remote_server_url`

## Bei Empfang von Remote-Server-Daten

Wird ausgelöst, wenn Daten von einem verbundenen Remote-Server empfangen werden.

Variablen:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Bei Remote-Server-Verbindung geschlossen

Wird ausgelöst, wenn eine Remote-Server-Verbindung geschlossen wird.

Variablen:

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Verbindungsverhalten

- Verbindungen werden **vom Client initiiert**
- FancyMenu hält Verbindungen im Hintergrund aktiv
- Wenn eine Verbindung abstürzt oder ein Timeout auftritt, versucht FancyMenu es alle 10 Sekunden erneut
- Wenn eine abgestürzte Verbindung wiederhergestellt wird, protokolliert FancyMenu eine Wiederherstellungsnachricht
- Ausgehende, noch nicht gesendete Nachrichten werden mit einer **maximalen Altersgrenze von 30 Sekunden** in eine Warteschlange gestellt
- Nachrichten in der Warteschlange, die älter als 30 Sekunden sind, werden verworfen

# URL-Modi

- `wss://` = sicher (TLS), empfohlen
- `ws://` = unverschlüsselt, nützlich für lokale Tests

Beispiel für eine lokale URL:

- `ws://127.0.0.1:8765`

# Best Practices

1. Verwenden Sie pro Backend-Dienst eine stabile URL.
2. Halten Sie das Nachrichtenformat für jeden Anwendungsfall konsistent.
3. Behandeln Sie geschlossene/abgestürzte Verbindungen mit Fallback-UI-Logik.
4. Verwenden Sie Schließen-Aktionen, wenn Ihr Ablauf abgeschlossen ist.
5. Verwenden Sie `wss://` für Produktionsumgebungen.
