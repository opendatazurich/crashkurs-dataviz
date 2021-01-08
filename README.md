Einfache Datenanalyse und -visualisierung mit Excel und Datawrapper
==============================================

## Fragestellung: «Stimmt es, dass es in Zürich in den meisten Stadtquartieren mehr Hunde als Kleinkinder gibt?»

Während dieses Kurses gehen wir dem Gerücht nach ob in den meisten Stadtquartieren tatsächlich mehr Hunde als Kleinkinder leben. Wir werden mit Open Data dazu die Fakten checken und zeigen, wie wir die gewonnenen Erkenntnisse darstellen und sogar als interaktive Webgrafiken visualisieren können.

Damit wir diese Fragestellung einfach und mit für alle Kursteilnehmenden vorhandenen Tools beantworten können, haben wir uns für Excel und [Datawrapper](https://www.datawrapper.de/) entschieden. 

## Teil 1: Daten finden und beziehen
Zur Beantwortung dieser Fragestellung benötigen wir die dazu relevanten Daten. Wir müssen uns also zuerst auf die Suche machen, wo wir die Anzahl Hunde und die Anzahl Kleinkinder pro Stadtquartier und Jahr beziehen können. Wie gut also, dass es in der Stadt Zürich einen [Open Data Katalog](https://data.stadt-zuerich.ch/) gibt, auf dem alle frei verfügbaren Verwaltungsdaten aufgelistet, ausführlich beschrieben und einfach durchsuchbar zum Download vorliegen ;)

- **Schritt 1:** Rufe den Open Data Katalog der Stadt Zürich auf unter: https://data.stadt-zuerich.ch/ 
- **Schritt 2:** Suche nach Hundebestand pro Stadtquartier und Jahr. Gebe dazu im Suchfeld beispielsweise den Begriff «Hunde» und «Stadtquartier» ein. Beim Eintippen des Suchbegriffs werden bereits passende Vorschläge zu auf dem Katalog vorkommenden Daten angezeigt.  
<img src="https://user-images.githubusercontent.com/2479732/103986721-847caf80-518b-11eb-839c-95953ead6f67.png" alt="Suchresultatvorschau" width="600"/>

- **Schritt 3:** 
  - Wähle das Dataset «[Hundebestand der Stadt Zürich](https://data.stadt-zuerich.ch/dataset/sid_stapo_hundebestand)» aus und lies die Metadaten dazu. Besonders wichtig sind dabei die Attributbeschreibungen, welche die Ausprägungen der Informationen im Datensatz beschreiben. Hier sehen wir beispielsweise, dass es Angaben zu Hundehaltenden und Hunden gibt. Bereits in der ersten Attributbeschreibung zur technischen Identifikationsnummer der hundehaltenden Personen erfahren wir bereits eine sehr wichtige Info, nämlich, dass ein Record (eine Zeile) in einem Datensatz einem Hund entspricht. Wenn also der gleiche Hundehaltende zwei Hunde hat, kommt seine ID hier auch zweimal vor. Dank der Beschreibung können wir auch sicher sein, dass die Stadtquartiere in den Daten vorkommen. Weiterführende wichtige Informationen sind auch unter *Bemerkungen* zu finden. 
  - Die Datensätze selber sind unter *Daten und Ressourcen* zu finden. Wähle dort den aktuellsten Datensatz (2020) aus und klicke darauf. 
  - Dadurch öffnet sich eine neue Webseite, welche den Downloadlink und eine einfache Datenvorschau beinhaltet.
  - Um die Daten herunter zu laden, klicke nun auf den Downloadlink. 
  <img src="https://user-images.githubusercontent.com/2479732/103988953-3669ab00-518f-11eb-99ab-0ca362d5cb0c.gif" alt="Dataset anschauen und Ressource downloaden" width="600"/>
  
- **Schritt 4:** Suche nach einem Datensatz, der die Anzahl Kleinkinder pro Stadtquartier und Jahr beinhaltet. Da für die Definition eines Kleinkindes das Alter relevant ist, suchen wir also einen Datensatz, welcher das Alter der Bevölkerung nach Stadtquartier und Jahr beinhaltet. Gib daher im Suchfeld beispielsweise die Begriffe «Alter» und «Stadtquartier» ein. Als [Suchresultat](https://data.stadt-zuerich.ch/dataset?q=alter+stadtquartier&sort=score+desc%2C+date_last_modified+desc) erscheinen nun aber 35 Datensätze. Wir sollte daher noch einen besseren Begriff wählen. Verwende daher besser die Begriffe «Altersjahr» und «Stadtquartier», dann sind es nur noch 8 [Resultate](https://data.stadt-zuerich.ch/dataset?q=altersjahr+stadtquartier&sort=score+desc%2C+date_last_modified+desc).

- **Schritt 5:** Für unsere Fragestellung ist der Datensatz «[Bevölkerung nach Stadtquartier, Herkunft, Geschlecht und Alter, seit 1993](https://data.stadt-zuerich.ch/dataset/bev_bestand_jahr_quartier_alter_herkunft_geschlecht_od3903)» am geeignetsten. Er beinhaltet zwar mehr Informationen als wir benötigen (die Herkunft oder das Geschlecht interessieren uns eigentlich weniger), aber wir werden sie in einem späteren Schritt mit Excel herausfiltern.
 



Für diesen Kurs verwenden wir CSV-Dateien.
CSV steht für **C**omma-**s**eparated **v**alues (komma-getrennte Werte).
Es ist ein sehr verbreitetes Format für tabellarische Daten.
CSV-Dateien haben meistens auf der ersten Zeile eine Spalteüberschrift und auf den nachfolgenden Zeilen dann die Werte.

![Struktur einer CSV-Datei](https://user-images.githubusercontent.com/538415/102370847-d6cc1580-3fbd-11eb-978c-ed6bbf146606.png)


Wir werden später dann lernen, wie man CSV-Datein in Excel importieren kann.
Im ersten Schritt geht es aber darum, CSV-Datei zu finden und herunterzuladen.

### Daten finden

Die offenen Behördendaten der Stadt Zürich (OGD - Open Government Data) werden auf dem OGD-Katalog angeboten: [http://data.stadt-zuerich.ch](http://data.stadt-zuerich.ch)

![OGD-Katalog der Stadt Zürich](https://user-images.githubusercontent.com/538415/102369942-cff0d300-3fbc-11eb-86f1-83264cdee019.png)

Andere Quellen sind zum Beispiel das [Geoportal](https://www.stadt-zuerich.ch/geodaten/) oder [opendata.swiss](https://opendata.swiss)


## Teil 2: Excel

### Daten in Excel laden

Excel starten...
![Excel-Screenshot](https://user-images.githubusercontent.com/538415/103784534-5c316b80-503a-11eb-94d7-bf8a04fcc4c2.png)

Alternative als HTML: <img src="https://user-images.githubusercontent.com/538415/103784534-5c316b80-503a-11eb-94d7-bf8a04fcc4c2.png" alt="Excel Screenshot" width="50"/>


### Auswertung in Excel erstellen

## Teil 3: Datawrapper

### Daten in Datawrapper laden

Datawrapper bietet einen Wizard an, um die Daten zu laden:

![Wizard von Datawrapper um Daten zu laden](https://user-images.githubusercontent.com/538415/102371585-9e790700-3fbe-11eb-966d-58f22547fd1c.png)
