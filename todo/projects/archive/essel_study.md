# TODOS:
* [X] remove `na.locf()` in `data.R`
* [X] calc the max warmup of both datasets
* [X] use filechecks.R everywhere
* [X] redo experiment: 6s qc
* [X] global filenames
* [X] Aufwand an DUALIS senden
* [X] require enter for input fields
* [X] (20.07.) Modelle hochladen, 13 Maschinen Modell verwenden
* [X] alle Statistiken in einen Tab packen
* [X] QC -> Scatterplot (others too?)
* [X] add summary to box stacker view
* [X] add new machines in read.R
* [X] Umstellung auf neues Statisikmodell
* [X] add new filechecks for new files (app)
* [X] ! validate: lifter -> IntervalIdlePercentage correct?
* [X] add old machine statistics to model
* [X] implement new machine File
* [X] bug: piecharts not individually scaled
* [X] Visualisation of Boxcount at machines
* [X] fullscreen feature?
* [X] loading spinners on recalculation

# Simulationsstudie

* [X] (2:45) erste Datenerfassung: (ohne Zuarbeit von Benjamin)
    * [X] (30 min) Maschinen: Prozesszustand (ohne Wartegrund) 
    * [X] (30 min) Lager: Paletten in und output
    * [X] (15 min) Transferdeckelsumme herausschreiben
    * [X] (30 min) Takt an QS Station 
    * [X] (30 min) Lifter: Zustand herausschreiben
    * [X] (30 min) Box Stacker: Menge der Kisten
* [X] (3:30 | bis: 29.06.) Anforderung von Boxen:
    * [X] (1:00) Verschiedene Läufe mit 3 - 8 Vorlaufkisten
    * [X] (0:30) einlesen der Daten 
    * [X] (0:30) %idle pro Maschine 
    * [X] (1:30) Visualisierung 
    * [X] Startzeitenanalyse mit richtigen Daten
* [X] (2:30 | bis 29.06.) Lager: Paletten
    * [X] (0:30) einlesen Daten (Lauf mit perfekter Kistenabstimmung)
    * [X] (0:30) Berechnung Lagerstand  
    * [X] (0:30) Visualisierung Lagerstand über Zeit
    * [X] (1:00) Visualisierung In and Out Boxplot pro Zeiteinheit
* [X] ( dualis ) Modell + zweite Datenerfassung (Zuarbeit Benjamin)
* Milestone: Modell final + Datenerfassung fertig
* [X] (0:30) Boxanforderung: Entfernen von idle Zeit am Prozessbeginn
* [X] (1:00) Paletten: Auftrennung nach Typen
* [X] (2:00) Transferdeckel:
    * [X] (0:30) einlesen der Daten 
    * [X] (0:30) Berechnung der Summe über die Zeit 
    * [X] (1:00) Visualisierung (Zeitstrahl + Boxplot nach Einschwingen)
* [X] (3:30) Bottleneck (QS Station):
    * [X] (0:30) Einlesen der Taktdaten
    * [X] (0:30) Visualisierung Boxplot 
    * [X] (0:30) Test: Abarbeitungszeit auf oberes Quantil/Max setzen
    * [X] (1:00) Warteschlange bauen + Länge messen
    * [X] (1:00) Test 2: Abarbeitungszeit in Stufen zwischen Mittelwert und Max setzen
    * [X] Visualisierung Warteschlange
* [X] (2:00) Auslastung Lifter:
    * [X] (0:30) Einlesen Zustandsdaten
    * [X] (0:30) Berechnung der prozentualen Verteilung
    * [X] (0:30) Visualisierung: Kuchendiagramm
    * [X] (0:30) Test: Werte bei verändertem auto homing
* [X] (2:30) Box Stacker:
    * [X] (0:30) Einlesen Kistenmengen und Typ
    * [X] (1:00) Berechnung: Anzahl Kisten nach Rang / Zeit
    * [X] (1:00) Visualisierung: mehrere Boxplots
    * [X] (0:30) exportierte Daten einlesen
    * [X] (0:30) daten in tidy format bringen
    * [X] (1:30) Visualisierung (stacked Area)
* [X] (2:00) Loop:
    * [X] (0:30) Einlesen Füllstand nach Typen
    * [X] (0:30) Berechnung Durchschnittswerte nach Warmlaufen
    * [X] (1:00) Visualisierung: Tortendiagramm oder Zeitverläufe
* [X] Lager Output in Richtung der Anlage:
    * [X] (1:00) Daten: statistik erstellen, Daten erfassen
    * [X] (0:30) calc: Output  
    * [X] (1:00) Visualisierung
* Milestone: Auswertung vollständig
* [X] (2:00) Visualisierung: Implementierung Vergleichsmöglichkeit
* [X] (3:00) Szenario: Maschinenanzahl
    * [X] (1:30): Erstellen der Modelle
    * [X] (1:00) Durchführen der Szenarien
    * [X] (0:30) Zusammenfassen der Ergebnisse
* [ ] (1:30) Szenario: extra Sammelkunde
    * [ ] (0:30) anpassen der Daten
    * [ ] (0:30) Durchführen der Szenarien
    * [ ] (0:30) Zusammenfassen der Ergebnisse
* [X] (2:30) Szenario: zufällige Produktionszeiten
    * [X] (1:30): Erstellen der Modelle, anpassen der Excel Sheets
    * [X] (0:30) Durchführen der Szenarien
    * [X] (0:30) Zusammenfassen der Ergebnisse
* [X] (1:30) Szenario: Vorproduktion der Boxen
    * [X] (0:30) Anpassung Modell
    * [X] (0:30) Durchführen der Szenarien
    * [X] (0:30) Zusammenfassen der Ergebnisse
* [X] (1:30) Szenario: linespeed
* [ ] (1:30) Szenario: Quality control
    * wird an den Maschinen eingetragen
* Milestone: Szenarien fertig

# refactor 1
* [X] divide code into: app, (console), (doc), base,
* [X] unified naming scheme
* [X] implement console startup code
* [X] make components usable in plain R:
    * [X] data reading
    * [X] data calculation
    * [X] plotting
* [X] make common schemes reusable
    * [X] data reading  
    * [X] file checking
    * [X] visualization
* [X] backup/SVN

# r server
* [X] install R and all packages
* [X] pull svn
* [X] start servers
* [X] make accessible
* [X] test

# meeting 06.08
* [X] vpn connection (Lütkemeier, Nieke)
    * email: + .csv export
* [X] VC neuinstall
* [X] box stacker:
    * [X] check calculations
    * [X] max --> time and product
* [X] warehouse:
    * [X] + verschlusskommissionierung
    * [X] in- and output: + output to line  
    * [X] in and out: 2 modi (directed, load)
    * [X] summary: +output
* [ ] documentation: statistic

# meeting 24.08.
* [X] zu viele caps ausgelagert
* [X] standardmodell 2x linespeed, weibull
* [X] machines tab: tuben pro tag pro maschine
