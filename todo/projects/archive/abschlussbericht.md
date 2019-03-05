# Abschlussbericht

## Inhalte  
* [X] (1:00) fachl. Inhalte
* [X] (1:00) Zeitplanung
* [X] (0:30) Weiterfuehrende Bildung
* [X] (0:30) Oeffentlichkeitsarbeit
* [X] (0:30) Netzwerke

## Formulierung
* [X] (0:30) fachl. Inhalte
* [X] (0:30) Zeitplanung
* [X] (0:15) Weiterfuehrende Bildung
* [ ] (0:15) Oeffentlichkeitsarbeit
* [ ] (0:15) Netzwerke

## Abgabe
* [ ] Korrekturlesen
* [ ] Unterschrift Dirk
* [ ] Unterschrift Nagel
* [ ] Abgabe

## fachl. Inhalte

### Themen
* Laufzeitoptimierung
    * Speicherorganisation (`__launch_bounds__`, MemConfig)
    * verschiedene Varianten verglichen (Daten in Register, SMem, global Mem), Ausgleichen von occupancy und schnellen Zugriff
    * unabh. Erzeugen von Zufallszahlen (vs. bulk generierung + Zwischenspeicherung)
    * sparsamere Datentypen, wo moeglich
    * Profiling und Testen
* Dimensionsreduktion zur Verteilung der Gewichte
    * Ziel: beliebige Anzahl von optimierungskriterien verarbeiten
    * multidimensional scaling
    * Zuordnung der Knoten reduzierten 2D Graphen auf einen Grid (Repraesentation des Speichers)
    * Integration in McEA
    * Visualisierung des Ergebnisses
    * Verbessern der Laufzeit + Speicherintensitaet
        * Nutzen von anderen dimensionsreduktions mechanismen (adagio, lnsolve, lgl)

### Durchfuehrung
* Implementierung: stop der Berechnungen nach abgelaufener Zeit 
    * verarbeiten von externen Signalen
    * refactoring: Struktur zur Wiederverwendung von Programmcode zwischen den Varianten
    * Implementierung dieser Funktion in die Vergleichsalgorithmen (+ Parametrisierung)
* Automatisierung der Uebersetzung des Codes
    * globales Konfigurationsschema
    * automatische Uebersetzung aller Konfigurationsvarianten
* Dokumentation aktualisieren
    * Neustrukturierung
    * Aktualisierung der Informationen, die von Aenderungen betroffen sind
    * neu: Installationsanweisungen, Grundablauf des Algorithmus, Speicherstruktur, Optimierungen, Gewichtung, unterstuetzte Optimierungsprobleme, Parametrisierung
* Experimente und Auswertung
    * Planung der benoetigten Experimente + aufzunehmenden Daten + Struktur
    * Implementierung eines automatisierten Datenreaders
    * Statistik: refactoring der vorhandenen Komponenten (Lesbarkeit, Wiederverwendung)
        * Erweiterung der Metriken um die Laufzeit

### Ergebnisse
* Dimensionsreduktion zur Verteilung der Gewichte
        * durch den hohen Speicherbedarf kann nur lgl verwendet werden
        * dort zeigt sich eine zu hohe Laufzeit (mehrere Tage zur Berechnung von Gewichtungen bei grosser Population)
        * daher leider unpraktikabel und nicht fuer McEA zu verwenden
* alle funktionserweiterungen und Umstrukturierungen haben einen deutlich vereinfachten und beschleunigten Arbeitsablauf möglich gemacht
* durch die Laufzeitoptimierung konnte die Geschwindigkeit noch in kleinem Maß verbessert werden.

### Auswirkungen
    * Viel Zeit wurde auf die Entwicklung und Verbesserung des Moduls zur Dimensionsreduktion verwendet
    * da dieses leider nicht den praktischen Anspruechen genuegt, muss eine andere Loesung gefunden werden  
    * dafuer wird noch weitere Zeit benoetigt

## Zeitplanung

* durch die Verzoegerungen, die die fachlichen Inhalte hervorrufen
    * extra Forschung an Dimensionsreduktion
* und Zusammenarbeit mit essel und DUALIS (siehe: Netzwerke) in einem Produktionsoptimierungsprozess
    * extra Aufwand, aber dafür Daten aus der Praxis und die Möglichkeit zur Anwendung
* Dissertation verschiebt sich nach hinten
* weiterhin ist die Finanzierung des Vorhabens nicht gesichert
    * daher: Arbeit an einem anderen Projekt an der HTW Dresden 
    * Zusicherung von 1em Tag pro Woche fuer die Promotion
* diese Einflussfaktoren fuehren zu einem angepassten Zeitplan  
    * welcher zu diesem Zeitpunkt noch mit dem Betreuer an der HTW Dresden (Prof. Nagel) abgesprochen werden muss 
* Veroeffentlichung der bisherigen Ergebnisse zu Ende 2018 (GA Tagung) und Anfang 2019 (HPC Tagung)
* Statusvortrag: Mitte 2019
* Abgabe der Doktorarbeit: Mitte 2020
* dieser Plan haengt aber an der Vorraussetzung, dass ab jetzt keine grundlegende inhaltliche Arbeit mehr zu leisten ist  
    * das muss mit Prof. Nagel noch abgesprochen werden 

### Oeffentlichkeitsarbeit
* Vortrag: GPU Optimierung von McEA (TU Dresden)
    * Vorlesung: 'Hochparallele Programmierung von GPUs' mit Matthias Werner
    * 30 min.
    * 22.01.
    * Information zu weiterführenden Themen und Projekten im Themenbereich GPU Programmierung 
    * Fokus auf Optimierung des GA, Darstellung des Fortschritts bei McEA
    * Zielgruppe: Informatikstudenten an der TU Dresden

### Netzwerke 
* Kontakt zu Karsten Wendt (GUIDES)
    * im Projekt wurde Multidimensional Scaling eingesetzt
    * Idee: Verwenden dieser Technik um Gewichtsverteilung im 2D Raum vorzuberechnen
    * Ausgang: siehe inhaltliche Darstellung
* Zusammenarbeit mit essel
    * Tubenhersteller aus Dresden 
    * Planung einer Restrukturierung/Erweiterung der Fertigung
    * vorab: Simulation, Auswertung und Optimierung des Plans
    * Simulation erstellt durch DUALIS  
    * Auswertung und Optimierung durch mich 
    * weitere Zusammenarbeit  
    * wertvolle Beispieldaten zur weiteren Verwendung/Evaluation von McEA

### Weiterfuehrende Bildung 
* Vorlesungsreihe: Genetische Algorithmen und Hochleistungsrechnen zur Produktionsplanung
    * Festlegen der zu behandelnden Themen
    * Vorbereiten der Vorträge und der begleitenden Unterlagen
    * Erstellen der Praktikumsaufgaben und Musterlösungen
    * Halten der Vorlesung und des Praktikums
    * Auswerten der Ergebnisse des Praktikums
    * eine Evaluierung der Lehrveranstaltung mit dem Betreuer
* Betreuer: Prof. Dr. rer. pol. Dirk Reichelt
* Umfang: 	4 Veranstaltungen à 1,5 Stunden, Vorbereitungszeit: 9 Stunden, 		Nachbereitungszeit: 3 Stunden
* keine anderen Maßnahmen zur weiterführenden Bildung
