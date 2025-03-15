|               |                                     |                                        |
| ------------- | ----------------------------------- | -------------------------------------- |
| **Modul 321** | **Verteilte Systeme programmieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

- [1. Verteilte Systeme](#1-verteilte-systeme)
  - [1.1. Was ist ein verteiltes System](#11-was-ist-ein-verteiltes-system)
  - [1.2. Merkmale eines verteilten Systems](#12-merkmale-eines-verteilten-systems)
  - [1.3. Kommunikation und Koordination](#13-kommunikation-und-koordination)
  - [1.4. Typen verteilter Softwaresysteme](#14-typen-verteilter-softwaresysteme)
  - [1.5. Vorteile verteilter Softwaresysteme](#15-vorteile-verteilter-softwaresysteme)
  - [1.6. Anwendungen und Beispiele](#16-anwendungen-und-beispiele)
- [2. Aufgaben](#2-aufgaben)
  - [2.1. Recherche zu verteilten Systemen](#21-recherche-zu-verteilten-systemen)

---

</br>

# 1. Verteilte Systeme

## 1.1. Was ist ein verteiltes System

- **Verteilte Softwaresysteme** bestehen aus einer Sammlung von unabhängigen, miteinander verbundenen Computern oder Prozessoren, die gemeinsam an der Lösung einer Aufgabe arbeiten.
- Diese Systeme sind so gestaltet, dass sie über **ein Netzwerk miteinander kommuniziere**n und ihre Arbeit koordinieren, um die Aufgabe effizienter zu erledigen, als es ein einzelner Computer alleine könnte.

- Ein verteiltes Softwaresystem kann als ein Netzwerk von unabhängigen Knoten (z. B. Computern, Servern oder Geräten) betrachtet werden, die miteinander kommunizieren und Ressourcen teilen.
- Diese Knoten arbeiten zusammen, um eine Aufgabe zu erfüllen, wobei jeder Knoten in der Regel nur **einen Teil** der Arbeit übernimmt.
- Die **Kommunikation** und Koordination zwischen diesen Knoten sind **essenziell** für das Funktionieren des gesamten Systems.

[Umfangreichere Beschreibung](https://www.atlassian.com/de/microservices/microservices-architecture/distributed-architecture)

## 1.2. Merkmale eines verteilten Systems

- **Dezentralisierung**
  - Es gibt keinen zentralen Punkt der Kontrolle. Jeder Knoten arbeitet unabhängig, kommuniziert jedoch regelmässig mit anderen Knoten.
- **Transparenz**
  - Die Verteilung der Aufgaben und Daten ist für den Nutzer nicht sichtbar. Das System soll so erscheinen, als handele es sich um eine einzelne Einheit.
- **Fehlertoleranz**
  - Da verteilte Systeme mehrere Knoten beinhalten, ist es möglich, dass einzelne Knoten ausfallen, ohne dass das gesamte System zusammenbricht.

## 1.3. Kommunikation und Koordination

- Die Kommunikation zwischen den Knoten eines verteilten Systems erfolgt über ein Netzwerk.
- Diese Kommunikation ist oft **asynchron**, das bedeutet, dass ein Knoten eine Nachricht senden kann, ohne sofort eine Antwort zu erhalten.
- Es gibt verschiedene Kommunikationsprotokolle, die je nach Art des Systems verwendet werden.
- Diese können beispielsweise Remote Procedure Calls (RPC) oder Message Passing Interface (MPI) sein.

- Ein zentrales Thema in verteilten Softwaresystemen ist die Koordination. Knoten müssen synchronisiert werden, um konsistente Ergebnisse zu liefern.
- Dafür werden spezielle Algorithmen und Protokolle entwickelt, um Probleme wie Konsistenz und Verfügbarkeit zu lösen.
- Ein bekanntes Beispiel ist der **CAP-Satz** (Consistency, Availability, Partition Tolerance), der besagt, dass ein verteiltes System immer **nur zwei von drei Eigenschaften gleichzeitig garantieren kann**: Konsistenz, Verfügbarkeit und Partitionstoleranz.

## 1.4. Typen verteilter Softwaresysteme

Es gibt verschiedene Arten von verteilten Softwaresystemen, die sich je nach Anwendung, Architektur und Ziel unterscheiden:

- **Client-Server-Modelle**
  - In diesem Modell fungieren Server als zentrale Stellen, die Ressourcen oder Dienste anbieten, während Clients diese Ressourcen anfordern. Ein typisches Beispiel ist eine Webanwendung, bei der der Webserver Anfragen von Benutzern (Clients) bearbeitet.
- **Peer-to-Peer (P2P)**
  - In einem P2P-System arbeiten alle Knoten gleichberechtigt miteinander. Jeder Knoten kann sowohl Server- als auch Client-Rolle einnehmen. Beispiele hierfür sind Dateifreigabe-Dienste wie BitTorrent oder Blockchain-Technologien.
- **Cloud Computing**
  - Hierbei handelt es sich um verteilte Systeme, bei denen Ressourcen wie Rechenleistung, Speicher und Daten über das Internet bereitgestellt werden. Benutzer greifen auf diese Ressourcen zu, ohne sich um die zugrunde liegende Infrastruktur kümmern zu müssen.
- **Microservices**
  - In modernen Softwarearchitekturen, wie z. B. bei Microservices, werden Anwendungen in **kleine, unabhängige Dienste** unterteilt, die über ein Netzwerk kommunizieren. Jeder Dienst ist auf eine bestimmte Funktionalität spezialisiert und arbeitet autonom.

## 1.5. Vorteile verteilter Softwaresysteme

Verteilte Softwaresysteme bieten zahlreiche Vorteile, die sie in vielen modernen Anwendungen unverzichtbar machen:

- **Skalierbarkeit**
  - Durch die Hinzufügung weiterer Knoten kann die Leistung des Systems erweitert werden. Dies ist besonders wichtig in Cloud-Umgebungen, in denen Systeme je nach Bedarf skalieren können.
- **Fehlertoleranz und Ausfallsicherheit**
  - Da Aufgaben auf mehrere Knoten verteilt sind, ist das System robuster gegenüber Ausfällen einzelner Knoten. Selbst wenn ein Teil des Systems ausfällt, kann der Rest weiterarbeiten.
- **Leistungssteigerung durch Parallelität**
  - Aufgaben können parallel auf mehreren Knoten ausgeführt werden, was zu einer erheblichen Leistungssteigerung führt.
- **Flexibilität**
  - Verteilte Systeme können dynamisch angepasst werden, indem Ressourcen hinzugefügt oder entfernt werden, ohne dass die gesamte Infrastruktur neu aufgebaut werden muss.

## 1.6. Anwendungen und Beispiele

Verteilte Softwaresysteme sind in vielen Bereichen von entscheidender Bedeutung:

- **Internetdienste**
  - Die meisten grossen Webanwendungen und Plattformen wie Google, Facebook und Amazon basieren auf verteilten Systemen, um Milliarden von Anfragen zu verwalten und Daten in Echtzeit zu verarbeiten.
- **Cloud Computing**
  - Plattformen wie AWS, Google Cloud und Microsoft Azure bieten verteilte Systeme an, um Anwendungen zu hosten, Daten zu speichern und Rechenleistung zu liefern.
- **Blockchain und Kryptowährungen**
  - Diese Technologien basieren auf verteilten Systemen, bei denen Transaktionen in einem Netzwerk von Knoten validiert und gespeichert werden.
- **Echtzeit-Datenverarbeitung**
  - Systeme zur Verarbeitung von Big Data oder Stream-Verarbeitung, wie Apache Kafka und Apache Spark, nutzen verteilte Architekturen, um grosse Datenmengen in Echtzeit zu analysieren.

**Beispiele für verteilte Systeme:**

- Telekommunikationsnetze, die Mobilfunk- und Internetnetze unterstützen
- Grafik- und Videowiedergabesysteme
- Wissenschaftliche Berechnungen, z. B. Proteinfaltung und Genforschung
- Fluglinien- und Hotelreservierungssysteme
- Multiuser-Videokonferenzsysteme
- Kryptowährungs-Verarbeitungssysteme (z. B. Bitcoin)
- Peer-to-Peer-Dateiaustauschsysteme Verteilte
- Community-Computersysteme
- Multiplayer-Videospiele
- Globale, verteilte Einzelhändler und Lieferkettenmanagement

---

</br>

# 2. Aufgaben

## 2.1. Recherche zu verteilten Systemen

| **Vorgabe**         | **Beschreibung**                                                    |
| :------------------ | :------------------------------------------------------------------ |
| **Lernziele**       | Können die Hauptkomponenten in einem **verteilten System** benennen |
|                     | Zusammenhänge in einem verteilten Systemen erläutern                |
|                     | Ein verteiltes System mit den Systemkomponenten grafisch darstellen |
| **Sozialform**      | Gruppenarbeit                                                       |
| **Auftrag**         | siehe unten                                                         |
| **Hilfsmittel**     | [Wiki](https://de.wikipedia.org/wiki/Verteiltes_System)             |
| **Zeitbedarf**      | 90min                                                               |
| **Lösungselemente** | Markdown Dokument, Präsentation                                     |

**Auftrag:**

- Recherchiere im Internet nach **verteilten Softwarelösungen (Microservices)** und ermittle die darin eingesetzten System und Hauptkomponenten.
- Dokumentiere die konkreten Aufgaben der ermittelten Haupt- und Systemkomponenten schriftlich.
- Skizziere die Haupt- und **Systemkomponenten** grafisch und visualisiere die Kommunikation zwischen diesen (Big Picture).
- Zeige, in welcher Reihenfolge eine **Verarbeitung** zwischen den Komponenten stattfindet.
