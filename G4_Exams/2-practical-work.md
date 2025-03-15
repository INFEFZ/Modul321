|               |                                     |                                        |
| ------------- | ----------------------------------- | -------------------------------------- |
| **Modul 321** | **Verteilte Systeme programmieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

- [1. Prüfung - Projektarbeit "SkyBooker"](#1-prüfung---projektarbeit-skybooker)
  - [1.1. Organisation](#11-organisation)
  - [1.2. Ausgangssituation](#12-ausgangssituation)
  - [1.3. Allgemeine Anforderungen](#13-allgemeine-anforderungen)
    - [1.3.1. Flugplan-Service (**FlightService**)](#131-flugplan-service-flightservice)
    - [1.3.2. Flugbuchungs-Service (**BookingService**)](#132-flugbuchungs-service-bookingservice)
    - [1.3.3. Authentifizierungs-Service (**AuthService**)](#133-authentifizierungs-service-authservice)
  - [1.4. Sicherheitsanforderungen](#14-sicherheitsanforderungen)
    - [1.4.1. Zugriffssteuerung JWT](#141-zugriffssteuerung-jwt)
  - [1.5. Datenbankdesign](#15-datenbankdesign)
    - [1.5.1. Flugplan-Datenbank](#151-flugplan-datenbank)
    - [1.5.2. Flugbuchungsdatenbank](#152-flugbuchungsdatenbank)
    - [1.5.3. Authentifizierungsdatenbank](#153-authentifizierungsdatenbank)
  - [1.6. Testing \& Qualitätssicherung](#16-testing--qualitätssicherung)
  - [1.7. Veröffentlichung (Publish) der Microservices in Docker](#17-veröffentlichung-publish-der-microservices-in-docker)
    - [1.7.1. Docker-Containerisierung der Microservices](#171-docker-containerisierung-der-microservices)
  - [1.8. Zusammenfassung der Anforderungen](#18-zusammenfassung-der-anforderungen)
  - [1.9. Zusätzliche Anforderungen](#19-zusätzliche-anforderungen)
  - [1.10. Randbedingungen](#110-randbedingungen)
  - [1.11. Kurzpräsentation](#111-kurzpräsentation)
- [2. Bewertung](#2-bewertung)
  - [2.1. Notenskala](#21-notenskala)

---

</br>

# 1. Prüfung - Projektarbeit "SkyBooker"

## 1.1. Organisation

|                     |                                           |
| :------------------ | :---------------------------------------- |
| **Lernziele**       | Element 2, Gewichtung 50%                 |
| **Sozialform**      | Gruppenarbeit (max. 3 Mitglieder)         |
| **Auftrag**         | siehe unten                               |
| **Hilfsmittel**     | Internet                                  |
| **Zeitbedarf**      | 12h                                       |
| **Lösungselemente** | Vollständiges Projekt inkl.  Präsentation |

## 1.2. Ausgangssituation

Die Plattform **SkyBooker** soll eine globale **Flugbuchungs**- und **Ticketreservierungslösung** bieten, die in der Lage ist, **Flüge** von verschiedenen Fluggesellschaften zu verwalten und den **Passagieren** eine Möglichkeit zur Buchung und Verwaltung ihrer Flugreisen zu bieten.
Die Architektur der Plattform soll auf **Microservices** und einer skalierbaren Datenbankstruktur basieren, um eine hohe Verfügbarkeit und Flexibilität zu gewährleisten.

Die Plattform muss zwei Hauptarten von Buchungen unterstützen:

- **Flugplanverwaltung (Stammdaten der Flüge)**
- **Flugbuchung (Flugbuchungen der Passagiere)**

## 1.3. Allgemeine Anforderungen

Die Lösung muss auf einer **Microservices-Architektur** basieren um **Flexibilität** und **Skalierbarkeit** zu gewährleisten, in **ASP.NET Core/C#** entwickelt und
nachfolgende Bereiche abdecken.

### 1.3.1. Flugplan-Service (**FlightService**)

Verwaltung von Fluginformationen (Abflugzeiten, Fluggesellschaften, Routen, Verfügbarkeiten)

- **POST /api/flight**: Erfassung eines Flugs
- **GET /api/flight**: Abfrage aller Flüge
- **GET /api/flight/{id}**: Abfrage eines Flugs mit Id

### 1.3.2. Flugbuchungs-Service (**BookingService**)

- **POST /api/booking**: Erfassung einer Buchung
- **GET /api/booking**: Abfragen aller Passagierbuchungen (Name, Anzahl Tickets, usw.)
- **GET /api/booking/{id}**: Abfragen einer Passagierbuchungen (Name, Anzahl Tickets, usw.)

### 1.3.3. Authentifizierungs-Service (**AuthService**)

Registrierung und Authentifizierung von Benutzern (Passagieren)

- **POST /api/register**: Registrierung eines Benutzers
- **GET /api/login**: Login mit Sicherheitsmechanismen (JWT)

## 1.4. Sicherheitsanforderungen

Alle sensitiven Daten, insbesondere Passwörter, müssen **verschlüsselt** gespeichert werden.

### 1.4.1. Zugriffssteuerung JWT

Der Zugriff auf die Web-Methoden beim **Flugplan-Service** muss über **JWT-Authentifizierung** gesichert sein.

## 1.5. Datenbankdesign

Die Plattform benötigt eine robuste und skalierbare Datenbankstruktur, um alle relevanten Daten zu speichern.
Die in der Datenbank zu speichernden Daten sind bereits festgelegt und müssen **zwingend** eingehalten werden.

### 1.5.1. Flugplan-Datenbank

- Datenbankprodukt: **MongoDB**
- Collection: **flights**

| **Feldname**    | **Beschreibung**                         |
| :-------------- | :--------------------------------------- |
| id              | Key (Identity, Autowert)                 |
| flightId        | Flug-Nr.                                 |
| airlineName     | Airline-Name                             |
| source          | Abflugort                                |
| destination     | Ankunftsort                              |
| departure_time  | Abflugdatum                              |
| arrival_time    | Ankunftsdatum                            |
| available_seats | Verfügbarkeit (Anzahl der freien Plätze) |
| created_at      | Erstellungsdatum                         |
| updated_at      | Letzte Änderung                          |

### 1.5.2. Flugbuchungsdatenbank

- Datenbankprodukt: **MS-SQL Server**
- Tabelle: **Booking**

| **Feldname**       | **Beschreibung**         |
| :----------------- | :----------------------- |
| Id                 | Key (Identity, Autowert) |
| FlightId           | Flug-Nr.                 |
| PassengerId        | Passagier-Nr.            |
| PassengerFirstname | Passagier-Vorname        |
| PassengerLastname  | Passagier-Nachname       |
| TicketCount        | Anzahl Tickets           |
| CreatedAt          | Erstellungsdatum         |
| UpdatedAt          | Letzte Änderung          |

### 1.5.3. Authentifizierungsdatenbank

- Datenbankprodukt: **SQLite**
- Tabelle: **User**

| **Feldname** | **Beschreibung**         |
| :----------- | :----------------------- |
| Id           | Key (Identity, Autowert) |
| Username     | Benutzername             |
| EMail        | E-Mail                   |
| Password     | Passwort (verschlüsselt) |

## 1.6. Testing & Qualitätssicherung

Alle Microservices sollten mit **Unit Tests** abgedeckt werden.

## 1.7. Veröffentlichung (Publish) der Microservices in Docker

Die **Microservices** sollen in **Docker-Containern** verpackt und veröffentlicht werden, um eine konsistente und skalierbare Bereitstellung in verschiedenen Umgebungen zu gewährleisten.

### 1.7.1. Docker-Containerisierung der Microservices

Jeder **Microservice** wird in einem eigenen **Docker-Container** betrieben, um ihn von anderen Services zu isolieren
und eine skalierbare Architektur zu gewährleisten.
Die Implementierung von Docker in die Flugbuchungsplattform stellt sicher, dass die **Microservices** portabel, skalierbar und einfach zu verwalten sind.

## 1.8. Zusammenfassung der Anforderungen

| **Nr.** | **Beschreibung**                                                                       |
| :------ | :------------------------------------------------------------------------------------- |
| A1      | Flugplan-, Flugbuchungs- und Authentifizierungs-Service komplett implementiert         |
| A2      | Datenbanken zum Flugplan, Flugbuchung und Authentifizierung komplett erstellt          |
| A3      | Komplette Veröffentlichung der Microservices in Docker umgesetzt (Dockerfile, Compose) |
| A4      | JWT-Authentifikation implementiert                                                     |
| A5      | Die Web-API's vollständig nach Open-API (Swagger) dokumentiert                         |
| A6      | Unit-Test vorhanden und durchgeführt                                                   |
| A7      | Das Softwareprojekt ist über ein Git-Repository zu verwalten.                          |
| A8      | Projektplanung (Gantt) u. Arbeitsaufteilung mit Zeitplanung durchgeführt.              |

## 1.9. Zusätzliche Anforderungen

Zusatzpunkte für optionale Erweiterungen.
Zur Erreichung der max. Punktzahl müssen zwei optionale Anforderungen umgesetzt werden.
Es werden nur **zwei** zusätzliche Anforderungen bewertet.

| **Nr.** | **Beschreibung**                                                                                |
| :------ | :---------------------------------------------------------------------------------------------- |
| AO1     | Logging (Protokollierung), z.B. mit Serilog bei allen Microservices implementiert               |
| AO2     | Zugriff erfolgt über ein **API-Gateway** (Ocelot), zentraler Einstiegspunkt                     |
| AO3     | Integration **WhatsApp-API** bei Buchungserfassung, WhatsApp Benachrichtigung                   |
| AO4     | Kommunikation zwischen den Microservices (Flug u. Buchung) für FlugNr Validierung (HTTP Client) |
| AO5     | Validierung der max. Sitzanzahl bei Flugbuchungen (Verhinderung Überbuchung)                    |
| AO6     | Erweiterte sinnvolle Kommunikation zwischen den Microservices über Message Broker (RabbitMQ)    |

## 1.10. Randbedingungen

Es müssen folgende Randbedingungen eingehalten werden:

- Die Implementierung muss mit **ASP.NET** in **C#** erfolgen.
- Alle Microservice stellen eine API-Dokumentation mit **OpenAPI (Swagger)** bereit.
- **Postman** ist als Web-API Test-Tool zu verwenden.
- Der Datenbankzugriff hat über einen **OR-Mapper** zu erfolgen

## 1.11. Kurzpräsentation

Sie stellen Ihre Ergebnisse mittels einer Kurzpräsentation der Klasse vor, präsentieren Sie Ihre
Webseite in einer Live Demo und schliessen Sie Ihre Präsentation mit einem kurzen Fazit ab (lessons
learned).
Dauer der Kurzpräsentation : ca. 15-20 min

---

</br>

# 2. Bewertung

| **Bewertung**                                                          | **Punkte** |
| :--------------------------------------------------------------------- | :--------: |
| Entwicklungswerkzeug inkl. Verwaltungssystem (Repository) eingerichtet |     2      |
| Änderungen werden dokumentiert und festgehalten (commit)               |     2      |
|                                                                        |            |
| Coderichtlinien wurden eingehalten (Naming, Konventionen etc.)         |     2      |
|                                                                        |            |
|                                                                        |            |
| Microservice Flugplan-Service komplett                                 |     2      |
| Microservice Flugbuchungs-Service komplett                             |     2      |
| Microservice Authentifizierungs-Service komplett                       |     2      |
| Datenbank für Flugplan-Service komplett                                |     2      |
| Datenbank für Flugbuchungs-Service komplett                            |     2      |
| Datenbank für Authentifizierungs-Service komplett                      |     2      |
| Authentifikation implementiert (JWT)                                   |     2      |
| Veröffentlichung in Docker komplett durchgeführt                       |     2      |
| Validierung in Controller Funktionen korrekt (FluentValidation)        |     2      |
| API vollständig dokumentiert (OpenAPI, Swagger)                        |     2      |
| Postman Collection vorhanden                                           |     2      |
| Unit-Test vorhanden                                                    |     2      |
|                                                                        |            |
| **Optional Anforderungen**                                             |            |
| Anforderung 1                                                          |     4      |
| Anforderung 2                                                          |     4      |
|                                                                        |            |
| **Dokumentation**                                                      |            |
| Zeitplanung nach Gantt vorhanden u. realistisch                        |     2      |
|                                                                        |            |
| **Präsentation / Fachgespräch**                                        |            |
| Systematischer Aufbau der Präsentation / Inhalt / Medienvielfalt       |     2      |
| Gestaltung und Lesbarkeit der Folien                                   |     2      |
| Lösung vollständig erläutert                                           |     2      |
| Live-Demo                                                              |     2      |
| Fazit                                                                  |     2      |
|                                                                        |            |
| **Total**                                                              |     50     |

## 2.1. Notenskala

> Erreichte Punktzahl x 5 / Max. Punktzahl + 1 = Note (auf 1/10 Noten gerundet)
