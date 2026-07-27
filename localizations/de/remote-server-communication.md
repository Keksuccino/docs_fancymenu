---
title: Kommunikation mit Remote-Servern
description: >-
  Sende und empfange benutzerdefinierte Textdaten zwischen FancyMenu-Clients und
  externen Servern.
---

# Kommunikation mit Remote-Servern

Das System „Kommunikation mit Remote-Servern“ ermöglicht es FancyMenu-Clients, über WebSocket-Verbindungen mit externen Servern zu kommunizieren.

Alle Daten sind textbasiert:

- Reiner Text wird unterstützt
- JSON wird unterstützt (als normaler Text)

Jede Server-URL erhält während der Laufzeit eine zwischengespeicherte **Anforderungs-ID**.
FancyMenu verwendet diese ID, um die Verbindung zu verfolgen und sie in Listener-Variablen bereitzustellen.

# Kurzanleitung

1. Füge [**Mit Remote-Server verbinden**](#connect-to-remote-server) hinzu, wenn die Verbindung früh geöffnet werden soll.
2. Füge [**Daten an Remote-Server senden**](#send-data-to-remote-server) mit derselben URL hinzu.
3. Füge [**Bei Empfang von Daten vom Remote-Server**](#on-remote-server-data-received) hinzu, um auf Antworten zu reagieren.
4. Verwende [**Bei Verbindung mit Remote-Server**](#on-remote-server-connected) und [**Bei geschlossener Remote-Server-Verbindung**](#on-remote-server-connection-closed) für Logik zum Verbindungsstatus.
5. Schließe Verbindungen mit [**Remote-Server-Verbindung schließen**](#close-remote-server-connection) oder [**Alle Remote-Server-Verbindungen schließen**](#close-all-remote-server-connections).

# Aktionen

## Mit Remote-Server verbinden

Öffnet oder verwendet erneut eine Remote-Server-Verbindung, ohne Nutzdaten zu senden.

Eingabe:

- Remote-Server-URL

## Daten an Remote-Server senden

Verbindet sich (oder verwendet eine bestehende Verbindung erneut) und sendet Textdaten.

Eingaben:

1. Remote-Server-URL
2. Daten

## Remote-Server-Verbindung schließen

Schließt eine Verbindung anhand der Anforderungs-ID.

Eingabe:

- Verbindungs-Anforderungs-ID

## Alle Remote-Server-Verbindungen schließen

Schließt alle aktuell aktiven Remote-Server-Verbindungen.

# Listener

## Bei Verbindung mit Remote-Server

Wird ausgelöst, nachdem eine Remote-Server-Verbindung erfolgreich geöffnet wurde.

Variablen:

- `$$request_id`
- `$$remote_server_url`

## Bei Empfang von Daten vom Remote-Server

Wird ausgelöst, wenn Daten von einem verbundenen Remote-Server empfangen werden.

Variablen:

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Bei geschlossener Remote-Server-Verbindung

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
- Wenn eine Verbindung abstürzt oder ein Timeout auftritt, versucht FancyMenu alle 10 Sekunden erneut eine Verbindung herzustellen
- Wenn eine abgestürzte Verbindung wiederhergestellt wird, protokolliert FancyMenu eine Wiederherstellungsnachricht
- Ausgehende, noch nicht gesendete Nachrichten werden mit einer **maximalen Lebensdauer von 30 Sekunden** in eine Warteschlange eingereiht
- Nachrichten in der Warteschlange, die älter als 30 Sekunden sind, werden verworfen

# URL-Modi

- `wss://` wird wie geschrieben verwendet und wird empfohlen.
- `ws://` wird wie geschrieben verwendet und ist unverschlüsselt.
- `https://` wird in `wss://` umgewandelt.
- `http://` wird in `ws://` umgewandelt.
- Ein nackter Host wird mit `wss://` vorangestellt.
- Andere explizite URL-Schemata werden abgelehnt.

Bevorzuge explizite `wss://`-URLs. Beispiel für eine lokale URL:

- `ws://127.0.0.1:8765`

Verwende pro Dienst eine stabile URL, behandle die Listener-Zustände „geschlossen/abgestürzt“ und schließe Verbindungen, wenn sie nicht mehr benötigt werden.
