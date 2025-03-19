|               |                                     |                                        |
| ------------- | ----------------------------------- | -------------------------------------- |
| **Modul 321** | **Verteilte Systeme programmieren** | ![IPSO Logo](./x_gitres/ipso_logo.png) |

- [1. Docker mit .NET](#1-docker-mit-net)
  - [1.1. Was genau ist Containerisierung?](#11-was-genau-ist-containerisierung)
  - [1.2. Die wichtigsten Vorteile der Containerisierung](#12-die-wichtigsten-vorteile-der-containerisierung)
  - [1.3. Warum spielen Container in .NET eine wichtige Rolle?](#13-warum-spielen-container-in-net-eine-wichtige-rolle)
  - [1.4. Schritt-für-Schritt-Anleitung - Erstellen eines .NET-Anwendungscontainers](#14-schritt-für-schritt-anleitung---erstellen-eines-net-anwendungscontainers)
    - [1.4.1. Beispiel Dockerfile](#141-beispiel-dockerfile)
  - [1.5. Eigenschaftsgruppe hinzufügen und das Docker-Image erstellen](#15-eigenschaftsgruppe-hinzufügen-und-das-docker-image-erstellen)
  - [1.6. Docker Container starten](#16-docker-container-starten)
  - [1.7. Beispielbefehle zu docker run](#17-beispielbefehle-zu-docker-run)
  - [1.8. Docker Compose](#18-docker-compose)
    - [1.8.1. Vorteile von Docker Compose](#181-vorteile-von-docker-compose)
    - [1.8.2. Beispiel einer Docker-Compose Datei](#182-beispiel-einer-docker-compose-datei)
    - [1.8.3. Anwendung mit docker-compose up starten](#183-anwendung-mit-docker-compose-up-starten)
- [2. Aufgaben](#2-aufgaben)
  - [2.1. Tutorial: Containerize a .NET app](#21-tutorial-containerize-a-net-app)
  - [2.2. ASP.NET Core WebAPI in Docker Container erstellen](#22-aspnet-core-webapi-in-docker-container-erstellen)
  - [2.3. ToDo WebAPI in Docker Container erstellen](#23-todo-webapi-in-docker-container-erstellen)

---

</br>

# 1. Docker mit .NET

- Im heutigen Cloud-Native-Szenario ist die **Containerisierung** zum Eckpfeiler der modernen Anwendungsentwicklung geworden.
- Das bedeutet, dass Ihre Anwendung und ihre Abhängigkeiten als eine einzige portable Einheit verpackt werden, die in verschiedenen Umgebungen gleich funktioniert und die Bereitstellung erleichtert.

- Die Unterstützung für Containerisierung ist ein nativer Aspekt von .NET. Anwendungen können mit Tools wie **Docker** und **Kubernetes** sehr einfach entwickelt, bereitgestellt und skaliert werden.
- Es gibt verschiedene Anwendungen für die Containerisierung, egal ob man **Microservices**, **Webanwendungen** oder **APIs** entwickelt; sie wird zu einem Beschleuniger für den Arbeitsablauf und einem Verstärker der Skalierbarkeit.

## 1.1. Was genau ist Containerisierung?

- Die Containerisierung kann als eine leichtgewichtige Version der **Virtualisierung** angesehen werden, bei der die Anwendung zusammen mit ihren Abhängigkeiten in einem Container verpackt wird, der dann zu einer einzigen **portablen Einheit** wird.
- **Container** laufen daher zuverlässig in verschiedenen Umgebungen, was sie für moderne Cloud-native Anwendungen geeignet macht.

## 1.2. Die wichtigsten Vorteile der Containerisierung

**Portabilität**: Sie können denselben Container auf jedem einzelnen Rechner ausführen.
**Effizienz**: Der Host-OS-Kernel wird gemeinsam genutzt, was zu einem geringeren Overhead führt.
**Isolierung**: Jeder Container arbeitet in völliger **Isolation**, wodurch jede Art von Konflikten mit der Einrichtung verhindert wird.

## 1.3. Warum spielen Container in .NET eine wichtige Rolle?

Die native Unterstützung für die Containerisierung in **.NET** ermöglicht die einfache Erstellung und Bereitstellung von Anwendungen in Containern.

Im Folgenden werden die Vorteile von Containern für .NET-Anwendungen beschrieben:

- **Vereinfachtes Deployment**: Konsistente Bereitstellung von Anwendungen in verschiedenen Umgebungen.
- **Skalierbarkeit**: Nahtlose Skalierung von Anwendungen dank Orchestrierungstools wie Kubernetes.
- **DevOps-Integration**: Sie können CI/CD-Funktionen nutzen, um die Kompilierung und Optimierung des Codes zu automatisieren.

## 1.4. Schritt-für-Schritt-Anleitung - Erstellen eines .NET-Anwendungscontainers

- Erstellen Sie eine einfache .NET-Web-API
  - `dotnet new webapi -o MyContainerApp`
- Eine Dockerdatei hinzufügen
  - Ein **Dockerfile** ist ein Dokument, das angibt, wie ein Container-Image erstellt werden soll und eine Konfigurationsdatei bildet. Legen Sie Ihr Dockerfile sorgfältig im Stammverzeichnis des Projekts an.

### 1.4.1. Beispiel Dockerfile

```console
# Choose the official .NET image as your base.
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80

# Build application
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY . .
RUN dotnet restore
RUN dotnet build -c Release -o /app/build

# Publish application
FROM build AS publish
RUN dotnet publish -c Release -o /app/publish

# Create the last image.
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "MyContainerApp.dll"]
```

## 1.5. Eigenschaftsgruppe hinzufügen und das Docker-Image erstellen

In der Projektdatei (.csproj) müssen die Docker-Einstellungen hinzugefügt. werden.

```xml
//in .csproj filr under PropertyGroup section add below lines
<DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
<ContainerRepository>MyContainerApp</ContainerRepository>
```

```console
dotnet publish --os linux --arch x64 /t:PublishContainer -c Release
```

## 1.6. Docker Container starten

Beim Befehl `docker run` werden häufig verschiedene Parameter angegeben, um das Verhalten des Containers zu steuern.

Hier sind die wichtigsten und am häufigsten verwendeten Parameter:

| **Parameter**                         | **Beschreibung**                                            |
| :------------------------------------ | :---------------------------------------------------------- |
| **`-d`**                              | Startet den Container im Hintergrund (detached mode)        |
|                                       | **`docker run -d nginx`**                                   |
| **`--name <container_name>`**         | Weist dem Container einen benutzerdefinierten Namen zu.     |
|                                       | **`docker run --name mein-container nginx`**                |
| **`-e <ENV_VAR>=<value>`**            | Setzt Umgebungsvariablen im Container                       |
|                                       | **`docker run -e DATABASE_URL=mysql://user:pass@db mysql`** |
| **`-p <host_port>:<container_port>`** | Verbindet Ports des Containers mit dem Host.                |
|                                       | **`docker run -p 8080:80 nginx`**                           |
| **`-it`**                             | Startet den Container interaktiv mit einer Shell            |
|                                       | **`docker run -it ubuntu bash`**                            |
| **`--rm`**                            | Löscht den Container nach dem Beenden automatisch           |
|                                       | **`docker run --rm ubuntu`**                                |

## 1.7. Beispielbefehle zu docker run

```console
docker run -p 5063:8080 mycontainerapp

rem build
docker build -t basket.service:v1.0 -f Basket.Service\Dockerfile .
docker build -t weather-api --force-rm  -f ".\Dockerfile" .

rem example basket service
docker run -it --rm -p 8080:8080 basket.service:v1.0
docker run -it --rm -p 5100:8080 --name weather-api weather-api

rem example rabbitmq (message broker)
docker run -d --hostname rmq --name rabbit-server -p 8080:15672 -p 15672:15672 rabbitmq:3-management
```

## 1.8. Docker Compose

- **Docker Compose** ist ein Tool, mit dem man mehrere Container-basierte Anwendungen mit einer einfachen YAML-Datei (docker-compose.yml) definieren, starten und verwalten kann.
- Es erleichtert die **Orchestrierung** mehrerer Docker-Container, sodass sie miteinander kommunizieren und gemeinsam als eine Anwendung arbeiten können.

### 1.8.1. Vorteile von Docker Compose

- **Vereinfachtes Management**: Statt mehrere docker run-Befehle auszuführen, reicht ein **einziger Befehl** (`docker-compose up`).
- **Mehrere Container gleichzeitig starten**: Perfekt für **Microservices**-Architekturen (z. B. Web-App + Datenbank + API-Gateway).
- **Netzwerkkonfiguration automatisch geregelt**: Container können sich untereinander über den Service-Namen ansprechen.
- **Umgebungsvariablen einfach verwalten**: Konfiguration kann über .env-Dateien erfolgen.
- **Portabilität**: Die gesamte Konfiguration kann in einer Datei gespeichert und auf verschiedenen Systemen ausgeführt werden.

### 1.8.2. Beispiel einer Docker-Compose Datei

```console
version: '3.8'

services:
  api:
    image: my-dotnet-api
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db
    environment:
      - ConnectionStrings__DefaultConnection=Host=db;Database=mydb;Username=admin;Password=secret

  db:
    image: postgres:latest
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret
    ports:
      - "5432:5432"
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

### 1.8.3. Anwendung mit docker-compose up starten

- Führen Sie den folgenden Befehl im gleichen Verzeichnis wie `docker-compose.yml` aus:
  - `docker-compose up -d`
- Status der laufenden Container prüfen
  - `docker-compose ps`

---

</br>

# 2. Aufgaben

## 2.1. Tutorial: Containerize a .NET app

| **Vorgabe**         | **Beschreibung**                                                                                                |
| :------------------ | :-------------------------------------------------------------------------------------------------------------- |
| **Lernziele**       | Können ein ASP.NET Core WebAPI Projekt erstellen                                                                |
|                     | Können für das Projekt ein korrektes **Dockerfile** erstellen                                                   |
|                     | Können das Projekt in Docker veröffentlichen                                                                    |
| **Sozialform**      | Einzelarbeit                                                                                                    |
| **Auftrag**         | siehe unten                                                                                                     |
| **Hilfsmittel**     | [Tutorial](https://learn.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=windows&pivots=dotnet-9-0) |
| **Zeitbedarf**      | 50min                                                                                                           |
| **Lösungselemente** | Lauffähiges Projekt in Docker Desktop                                                                           |

**Auftrag:**

- Arbeit das komplette [Tutorial](https://learn.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=windows&pivots=dotnet-9-0) durch und halte die wichtigsten Schritte für die Docker-Veröffentlichung fest.
  - Create and publish a simple .NET app
  - Create and configure a Dockerfile for .NET
  - Build a Docker image
  - Create and run a Docker container

---

## 2.2. ASP.NET Core WebAPI in Docker Container erstellen

| **Vorgabe**         | **Beschreibung**                                                                                                |
| :------------------ | :-------------------------------------------------------------------------------------------------------------- |
| **Lernziele**       | Können ein ASP.NET Core WebAPI Projekt erstellen                                                                |
|                     | Können für das Projekt ein korrektes **Dockerfile** erstellen                                                   |
|                     | Können das Projekt in Docker veröffentlichen                                                                    |
| **Sozialform**      | Einzelarbeit                                                                                                    |
| **Auftrag**         | siehe unten                                                                                                     |
| **Hilfsmittel**     | [Tutorial](https://learn.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=windows&pivots=dotnet-9-0) |
| **Zeitbedarf**      | 50min                                                                                                           |
| **Lösungselemente** | Lauffähiges Projekt in Docker Desktop                                                                           |

**Auftrag:**

- Erstelle ein Standard **ASP.NET Core WebAPI** (WeatherForecast) und veröffentliche das Beispielprojekt in **Docker**.
- Schreibe hierfür eine **Dockerfile** und teste die Applikation in Docker.
- Erstelle und veröffentliche die Anwendung mit einem Port-Mapping über das Dockerfile (Befehlszeile)
- Erstelle und veröffentliche die Anwendung über eine `docker-compose.yml` Datei (Befehlszeile).

---

## 2.3. ToDo WebAPI in Docker Container erstellen

| **Vorgabe**         | **Beschreibung**                                                                                                            |
| :------------------ | :-------------------------------------------------------------------------------------------------------------------------- |
| **Lernziele**       | Können ein ASP.NET Core WebAPI Projekt erstellen                                                                            |
|                     | Können für das Projekt ein korrektes **Dockerfile** File erstellen                                                          |
|                     | Können für das Projekt ein korrektes **Docker Compose** File erstellen                                                      |
|                     | Können das Projekt in **Docker** veröffentlichen                                                                            |
| **Sozialform**      | Einzelarbeit                                                                                                                |
| **Auftrag**         | siehe unten                                                                                                                 |
| **Hilfsmittel**     | [ASP.NET Core Series](hhttps://learn.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=windows&pivots=dotnet-9-0) |
| **Zeitbedarf**      | 50min                                                                                                                       |
| **Lösungselemente** | Lauffähiges Projekt in Docker Desktop                                                                                       |

**Auftrag:**

Erweitere die in den vorherigen Aufgaben gelöste TodoDTO App (siehe **Tutorial: Create a minimal API with ASP.NET Core with DTO (ToDo)**) wie folgt:

- Anstelle SQLite müssen die Daten (ToDo's) neu in einer **MS SQL-Server Datenbank** gespeichert werden.
- Die ToDo-WebAPI und die MS-SQL Datenbank müssen in Docker (composed) installiert und ausgeführt werden können.

**Gehe dabei wie folgt vor:**

- ToDo-WebAPI Projekt in Visual Studio auf MS-SQL Server migrieren
- **Dockerfile** für ToDo-WebAPI in erstellen
- **Docker Compose** für ToDo-WebAPI u. MS-SQL-Server erstellen
- Publish Docker-Compose (up)
- WebAPI-Testlauf mit Swagger oder Postman
