# Input
- Daten aus mehreren Quellen
- Verlaufsdaten

# Eigenschaften
- in Funktionsbereiche getrennt
- konsistent (trotz verschiedener Quellen)
- Betrachtung von Daten im Laufe der Zeit

# Ziel
- Visualisierung
- Analyse (Statistik, Berichte)
- Entscheidungsunterstützung
- Vorhersagen treffen (Data Mining)

# Design
- Metadaten, Zusammenfassungsdaten und Rohdaten im zentralen Repository
- optional Staging Bereich: Bereinigung der Daten
- optional Data Mart: zwischen Repo und Endnutzern
  - fertig vorbereitete Daten hierher verschoben
- optional: Operation Data Stores (ODS)
  - enthalten nur täglich benutzte Daten (kein Verlauf)
- Sandbox: außerhalb der Regeln und Protokolle des DW
  - nur für internen Gebrauch/Tests

## Themen
- Dateninhalt
- Beziehungen zwischen Daten
- Systemumgebung (Server)
- Software/Bibliotheken
- Datentransformationen
- Aktualisierungsfrequenz

## Komponenten
- relationale DB
- ETL (Extract, Transform, Load) 