|               |                                     |                                        |
| ------------- | ----------------------------------- | -------------------------------------- |
| **Modul 321** | **Verteilte Systeme programmieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

- [1. Prüfung - Präsentation zum Thema "Verteilte Systeme programmieren"](#1-prüfung---präsentation-zum-thema-verteilte-systeme-programmieren)
  - [1.1. Organisation](#11-organisation)
  - [1.2. Auftrag](#12-auftrag)
  - [1.3. Wichtig](#13-wichtig)
  - [1.4. Themenauswahl](#14-themenauswahl)
    - [1.4.1. Microservices in virtualisierten Umgebungen mit Docker](#141-microservices-in-virtualisierten-umgebungen-mit-docker)
    - [1.4.2. Message Broker RabbitMQ](#142-message-broker-rabbitmq)
    - [1.4.3. Einsatz von API-Gateways in Microservices mit Ocelot](#143-einsatz-von-api-gateways-in-microservices-mit-ocelot)
    - [1.4.4. Authentifizierung und Autorisierung in Microservices mit JWT](#144-authentifizierung-und-autorisierung-in-microservices-mit-jwt)
- [2. Bewertung](#2-bewertung)
  - [2.1. Notenskala](#21-notenskala)

</br>

# 1. Prüfung - Präsentation zum Thema "Verteilte Systeme programmieren"

## 1.1. Organisation

| **Vorgabe**         | **Beschreibung**                                                       |
| ------------------- | ---------------------------------------------------------------------- |
| **Lernziele**       | Element 1, Gewichtung 50%                                              |
| **Sozialform**      | Gruppenarbeit, max. 3 Mitglieder                                       |
| **Auftrag**         | siehe unten                                                            |
| **Hilfsmittel**     | Internet                                                               |
| **Zeitbedarf**      | Arbeit 3h, Präsentation 30min                                          |
| **Lösungselemente** | Vollständige Präsentation mit eigenen Beispielcode-Lösungen, Tutorials |

## 1.2. Auftrag

- Recherchieren Sie ein spezifisches Fachthema aus dem Bereich **"Verteilte Systeme programmieren"** und bereiten Sie eine Präsentation für die Klasse vor.
- Ihre Präsentation soll die wichtigsten Aspekte des Themas verständlich erklären und mit geeigneten Code- oder Übungsbeispielen veranschaulichen.

**Recherche:**

- Nutzen Sie verschiedene Quellen (Fachartikel, Online-Dokumentationen, offizielle Dokumentationen).
- Achten Sie auf verständliche Erklärungen und praxisnahe Anwendungen.

**Präsentation:**

- Strukturieren Sie die Inhalte logisch (Einführung, Hauptteil, Fazit).
- Erklären Sie Fachbegriffe und Konzepte verständlich.
- Verwenden Sie anschauliche Grafiken oder Diagramme zur Unterstützung.
- Fügen Sie Codebeispiele oder Übungsaufgaben zur Veranschaulichung ein.

**Vortrag:**

- Üben Sie Ihre Präsentation, um sicher und frei sprechen zu können.
- Bereiten Sie sich auf mögliche Fragen der Klasse vor.

**Abgabe:**

- Komplette Präsentation
- Codebeispiele oder Übungsbeispiele zum Download (GitHub)

## 1.3. Wichtig

- **Kein PowerPoint. Die Präsentation hat im Markdown Format zu erfolgen.**
- Dauer der Kurzpräsentation: **30 min**

---

</br>

## 1.4. Themenauswahl

### 1.4.1. Microservices in virtualisierten Umgebungen mit Docker

- Erstellen Sie eine detaillierte Präsentation zu den Möglichkeiten von Microservices in virtualisierten Umgebungen wie Docker.
- Zeigen Sie insbesondere, wie ASP.NET Core-Anwendungen in Visual Studio für Docker erstellt werden können.
- Erklären Sie die benötigten Voraussetzungen sowie die wichtigsten Konfigurationsdateien wie `Dockerfile`, .`dockerignore` und `docker-compose.yml`.

**Einführung in Microservices & Docker:**

- Was sind Microservices?
- Warum Docker für Microservices?
- Vorteile von Containern gegenüber klassischen Deployments
- Voraussetzungen für die Entwicklung in Visual Studio

**Voraussetzungen für die Entwicklung in Visual Studio:**

- Installation von Visual Studio mit Docker-Unterstützung
- Installation von Docker Desktop
- Einrichtung des ASP.NET Core-Projekts mit Docker-Support
- Erstellung einer ASP.NET Core-Anwendung mit Docker

**Erstellung einer ASP.NET Core-Anwendung mit Docker:**

- Schritt-für-Schritt-Anleitung zur Erstellung eines ASP.NET Core-WebAPI-Projekts mit Docker-Integration
- Konfiguration des Projekts für Containerisierung
- Testlauf der Anwendung in einem Docker-Container
- Erläuterung wichtiger Docker-Konfigurationsdateien

**Erläuterung wichtiger Docker-Konfigurationsdateien:**

- Dockerfile: Aufbau und Bedeutung der Befehle
- .dockerignore: Zweck und typische Inhalte
- docker-compose.yml: Mehrere Container orchestrieren (z. B. Web-App + Datenbank)

**Praktische Demonstration:**

- Container-Build-Prozess und Start mit docker build und docker run
- Nutzung von docker-compose up für mehrere Container
- Debugging und Logging von Containern

---

</br>

### 1.4.2. Message Broker RabbitMQ

- Zeigen Sie, wie **RabbitMQ** in ASP.NET Core WebAPI-Projekten eingesetzt wird.
- Erläutern Sie die Voraussetzungen, die verschiedenen Kommunikationsarten sowie typische Einsatzbereiche von **RabbitMQ** in Microservice-Architekturen.

**Einführung in RabbitMQ & Microservices:**

- Was ist **RabbitMQ**?
- Warum wird **RabbitMQ** in Microservices eingesetzt?
- Vorteile der asynchronen Kommunikation in Microservices

**Voraussetzungen für den Einsatz von RabbitMQ in ASP.NET Core:**

- Installation von **RabbitMQ** mit Docker oder lokal
- Installation von **RabbitMQ.Client** über NuGet
- Grundlagen der AMQP (Advanced Message Queuing Protocol)

**Kommunikationsarten mit RabbitMQ:**

- Einfaches Warteschlangenmodell (Point-to-Point)
- Publish-Subscribe (Fanout Exchange)
- Routing (Direct Exchange)

**Implementierung in ASP.NET Core:**

- Erstellung eines Producers (Sender) in einer WebAPI
- Erstellung eines Consumers (Empfänger) als eigenständigen Microservice
- Nutzung von `Dockerfile` und `docker-compose.yml` zur Containerisierung
- Fehlerbehandlung und **Retry-Mechanismen** in RabbitMQ

**Praktische Demonstration:**

- Senden und Empfangen von Nachrichten zwischen Microservices
- Nutzung der **RabbitMQ** Management-Oberfläche
- Skalierung durch mehrere Consumer-Instanzen

---

### 1.4.3. Einsatz von API-Gateways in Microservices mit Ocelot

- Zeigen Sie, wie API-**Gateways** mit Ocelot in ASP.NET Core WebAPI-Projekten eingesetzt werden können.
- Erläutern Sie die Voraussetzungen sowie die verschiedenen Einsatzbereiche von API-Gateways in Microservice-Architekturen.

**Einführung in API-Gateways & Microservices:**

- Was ist ein API-Gateway?
- Warum wird ein API-Gateway in Microservice-Architekturen benötigt?
- Vorteile eines API-Gateways (Routing, Load Balancing, Sicherheit, Monitoring)

**Voraussetzungen für die Nutzung von Ocelot in ASP.NET Core:**

- .NET Core/ASP.NET Core WebAPI
- Installation von Ocelot über NuGet
- Grundlagen von Reverse Proxy & Load Balancing

**Einsatzbereiche von API-Gateways in Microservices:**

- Routing & Weiterleitung von API-Anfragen
- Authentifizierung & Autorisierung (z. B. mit JWT oder IdentityServer)
- Lastverteilung und Load Balancing zwischen Services
- Caching und Anfrage-Limite (Rate Limiting)
- Service Discovery (z. B. mit Consul oder Eureka)

**Implementierung eines API-Gateways mit Ocelot:**

- Einrichtung eines Ocelot API-Gateways in ASP.NET Core
- Konfiguration von Routing und Weiterleitung in ocelot.json
- Anbindung mehrerer Microservices über Ocelot
- Absicherung des API-Gateways mit JWT-Authentifizierung
- Lastverteilung mit Ocelot Load Balancer

**Praktische Demonstration:**

- Aufbau einer Microservice-Architektur mit einem API-Gateway
- Testen der Weiterleitung über das API-Gateway
- Skalierung und Load Balancing demonstrieren
- Fehlerhandling und Logging mit Ocelot

---

</br>

### 1.4.4. Authentifizierung und Autorisierung in Microservices mit JWT

- Erstellen Sie eine detaillierte Präsentation über die Möglichkeiten der **Authentifizierung** und **Autorisierung** in Microservices.
- Zeigen Sie, wie **JWT (JSON Web Token)** für die **Authentifizierung** und **Autorisierung** in ASP.NET Core WebAPI-Projekten implementiert werden kann.
- Erläutern Sie die Voraussetzungen sowie den Einsatz von Datenbanken und **API-Gateways (Ocelot)** zur Sicherung der Microservice-Architektur.

**Voraussetzungen für die Implementierung:**

- ASP.NET Core WebAPI
- Datenbank (z. B. SQL Server, PostgreSQL, MongoDB) für Benutzerdaten
- Identity Management mit ASP.NET Core Identity
- API-Gateway mit Ocelot für zentrale Authentifizierung

**Implementierung der JWT-Authentifizierung in ASP.NET Core:**

- Erstellung eines WebAPI-Projekts mit Benutzer-Login & Token-Generierung
- Speicherung von Benutzerdaten in einer Datenbank
- Absicherung von Endpunkten mit `[Authorize]`-Attributen

**Integration mit API-Gateway (Ocelot):**

- Konfiguration von Ocelot für Authentifizierung & Autorisierung
- Weiterleitung von API-Anfragen nur mit gültigem JWT-Token
- Schutz eines Microservices durch das Gateway

**Praktische Demonstration:**

- Benutzerregistrierung und -login mit JWT
- Testen der geschützten Endpunkte mit Postman oder Swagger
- Debugging und Fehlerbehandlung in der Authentifizierung

**Zusammenfassung & Best Practices:**

- Vorteile und Herausforderungen der JWT-Authentifizierung
- Best Practices für sichere Implementierung in Microservices

---

</br>

# 2. Bewertung

| Bewertung                            | Punkte |
| :----------------------------------- | :----: |
| **Aufbau / Gliederung**              |   2    |
| - Systematischer Aufbau              |        |
| - Medienvielfalt                     |        |
| - Inhaltsverzeichnis                 |        |
| - Systematisch u. folgerichtig       |        |
| **Qualität**                         |   2    |
| - wesentliche Infos                  |        |
| - Gestaltung                         |        |
| - Lesbarkeit                         |        |
| **Quantität**                        |   2    |
| - Umfang u. Abdeckungsgrad           |        |
| - Länge angemessen                   |        |
| **Sachwissen**                       |   2    |
| - souveränder Vortrag                |        |
| - kompetente Antworten               |        |
| **Demo / Vorführung**                |   2    |
| - geeignetes Beispielprojekt gewählt |        |
| - grundlegende Funktion vorhanden    |        |
| - verständlich u. nachvollziebar     |        |
|                                      |        |
| Total                                |   10   |

## 2.1. Notenskala

> Erreichte Punktzahl x 5 / Max. Punktzahl + 1 = Note (auf 1/10 Noten gerundet)
