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
 
- **Schritt 6:** Lies nun auch wieder die Metadaten zum Datensatz und gehe gleich wie in **Schritt 3** vor, um den Datensatz auf Deinen Computer herunter zu laden.

- **Schritt 7:** Du hast nun die beiden für unsere Fragestellung relevanten Datensätze gefunden und heruntergeladen. Sie heissen `20200306_hundehalter.csv` (Hunde) und `BEV390OD3903.csv`(Bevölkerungsdaten). Kopiere diese beiden Datensätze nun aus dem Downloadverzeichnis Deines Computers und lege sie in ein Verzeichnis, wo Du  an den noch folgenden Schritten weiter arbeiten kannst. 

Damit ist nun unser erster Teil zu Daten finden und beziehen beendet. Solltest Du mal für eine andere Fragestellunng auf dem Open Data Katalog der Stadt Zürich nicht fündig werden, können auch viele andere Open Data Quellen konsultiert werden. Auf nationaler Ebene werden unter [opendata.swiss](https://opendata.swiss) Open Data von verschiedenen Bundesstellen, anderen Kantonen und Städten offene Verwaltungdaten angeboten. 

## Teil 2: Excel

### CSV... what?
Eines der Grundprinzipien von Open Data ist, dass die Datenstätze in **nicht-proprietären Formaten** veröffentlicht werden sollen. Sprich, für die Verwendung der Daten sollen die AnwenderInnen nicht auf kommerzielle Software setzen müssen. Damit soll allen die gleiche Möglichkeit gegeben werden, mit den Daten arbeiten zu können. Das Excelformat (.xls oder .xlsx) ist ein Beispiel eines proprietären Datenformats, weil es zur Verwendung Excel erfordert.

Das Standardformat für tabellarische Daten ist daher [CSV](https://de.wikipedia.org/wiki/CSV_(Dateiformat)). CSV steht für **C**omma-**s**eparated **v**alues (komma-getrennte Werte).

**Beispiel:** 

CSV-Dateien haben meistens auf der ersten Zeile eine Spaltenüberschrift und auf den nachfolgenden Zeilen dann die kommaseparierten Werte.
<pre>
"zeitpunkt","bruttolastgang","status"
"2020-01-01T00:15",66546.656045,"E"
"2020-01-01T00:30",66018.362440,"E"
"2020-01-01T00:45",65272.630020,"E"
"2020-01-01T01:00",64385.925397,"E"
"2020-01-01T01:15",63578.900426,"E"
"2020-01-01T01:30",63105.155989,"E"
"2020-01-01T01:45",62287.860786,"E"
"2020-01-01T02:00",61283.998490,"E"
</pre>

Werte zwischen Anführungszeichen sind entweder Texte oder Datumswerte. Wo keine Anführungszeichen stehen, handelt es sich um numerische Werte.  Die Kodierung für Unicode-Zeichen ist dabei standardmässig [UTF-8](https://de.wikipedia.org/wiki/UTF-8).
Dieser CSV-Auszug repräsentiert die folgende Tabelle:

![DarstellungExcel](https://user-images.githubusercontent.com/2479732/104014716-cc173180-51b3-11eb-9440-3d87d2fb6128.png)

### CSV-Datensätze in Excel laden

Vielleicht fragst Du Dich nun unterdessen, wozu der ganze Exkurs über CSV dienlich sein soll... Nun, leider ist es so, dass bereits zu diesem Zeitpunkt viele scheitern, die noch nie mit CSV gerarbeitet haben und eine CSV-Datei in Excel öffnen wollen. Daher zeigen wir Euch in diesem Abschnitt, wie man vorgehen sollte, wenn man mit CSV-Datensätzen in Excel arbeiten möchte.

**Wie es NICHT funktioniert:**
Ein Doppelklicken auf die CSV-Datei wie hier gezeigt funktioniert leider meistens nicht. Obwohl man gemäss des Icons der Datei das Gefühl hätte, dass dies doch so möglich sein sollte. Folgendes geschieht jedoch stattdessen: 

<img src="https://user-images.githubusercontent.com/2479732/104017881-32528300-51b9-11eb-8d15-39debf3c426a.gif" alt="ExcelFail" width="800"/>

Die CSV-Datei wird zwar in Excel geöffnet, es findet jedoch keine saubere Trennung der Attribute in einzelne Spalten statt (vgl. die oben gezeigte Tabelle). Mit der hier gezeigten Vorgehensweise sind alle Werte in eine Spalte (hier Spalte A) eingefügt worden. Damit lässt sich nicht bequem weiter arbeiten.

**Der Clou: CSV-Datei muss IMPORTIERT werden**

Damit ihr wie erwartet basierend auf einem CSV-Datensatz in Excel weiterarbeiten könnt, müsst ihr den CSV-Datensatz **importieren**. Dazu müsst ihr folgendermassen vorgehen:

- **Schritt 1:** Öffne eine neue leere Exceldatei und speichere Sie in Dein Verzeichnis, wo Du bereits die beiden CSV-Datensätze abgelegt hast ( `20200306_hundehalter.csv` und `BEV390OD3903.csv`). Gib dem Excelfile einen Namen, z.B. `Kleinkinder_und_Hunde.xlsx`.

- **Schritt 2:** Gehe zum Menu **Daten** und klicke auf **Externe Daten abrufen**. Wähle aus allen angezeigten Optionen **Aus Text** aus.

- **Schritt 3:** Mit dem Pop-Up **Textdatei importieren** wirst Du aufgefordert, die Textdatei auszuwählen, die Du nun ins Excelfile importieren möchtest. Wähle zuerst `20200306_hundehalter.csv` zum Import aus und klicke auf **Importieren**.

- **Schritt 4:** Nun erscheint das Pop-Up mit dem **Textkonvertierungs-Assistenten**, welcher dich durch drei Importschritte führt.
  - a) Wähle **Getrennt** aus, weil unsere Datensätze ja durch Kommas abgetrennt sind. Der Import beginnt in Zeile 1 und das CSV liegt in UTF-8 Kodierung vor. Aktiviere auch das Kästchen, dass die Datei Überschriften hat. Ganz unten siehst Du eine Vorschau, wie gemäss Deiner Auswahl der Import aussehen würde. Klicke nun auf **Weiter**.
  - b) Im nächsten Dialogfeld musst Du nun die Trennzeichen definieren. In unserem Fall, resp. bei CSV, sollte dies immer **Komma** sein. Wähle es aus und beobachte die Veränderung in der Vorschau. Wenn Du zufrieden bist, klicke auf **Weiter**.
  - c) Im letzten Dialogfeld kannst Du den Datentypen für jede Spalte definieren. Dies ist in den meisten fällen nicht notwendig. In unserem Beispiel wurde noch explizit das Attribut Alter als Text definiert. Dies weil gewisse Werte von Excel z.T. auch als Datum interpretiert werden. Wenn Du zufrieden bist, klicke auf **Weiter**.  
  
- **Schritt 5:** Bestätige mit **OK** den Import in das aktuelle Arbeitsblatt Deines Excelfiles. Voila, die Daten liegen nun so vor, dass Du mit den Hundedaten nun weiter arbeiten kannst.

<img src="https://user-images.githubusercontent.com/2479732/104021668-747ec300-51bf-11eb-859d-23aecceabee3.gif" alt="csvImport" width="800"/>

- **Schritt 6:** Überschreibe unten links den Arbeitsblattnamen von *Tabelle 1* auf *Hundebestand_2020*. Dies erfolgt einfach, indem Du auf den Text Tabelle 1 doppelklickst und ihn dann überschreibst.

- **Schritt 7:** Füge nun - mit einem Klick auf das Plus-Zeichen - ein neues Arbeitsblatt hinzu und nenne es *Bevölkerungsbestand*.
- **Schritt 8:** Importiere nun `BEV390OD3903.csv`wie ab Schritt 3 beschrieben in unser Excelfile `Kleinkinder_und_Hunde.xlsx`. Tipp: definiere beim Import die Spalte *AlterV05Kurz* als Text, weil sonst wirklich einzelne Werte als Datum dargestellt werden.

Damit sind wir fertig mit dem Datenimport. Unser Excelfile `Kleinkinder_und_Hunde.xlsx` beinhaltet nun zwei Arbeitsblätter mit den Hunde- und Bevölkerungsbestandsdaten, welche wir nun im nächsten Schritt analysieren werden.

<img src="https://user-images.githubusercontent.com/2479732/104026534-5a94ae80-51c6-11eb-8940-1b2ffcca7f3a.gif" alt="abschlussDatenImports" width="800"/>

### Datenauswertung mit Excel 
Excel ist bezüglich Datenanalyse selbstverständlich nicht allererste Sahne. Fortgeschrittenere AnwenderInnen verwenden in der Regel mächtigere Statistiktools wie **[R](https://www.r-project.org/)** (siehe dazu Ressourcen, wie [Rddj](https://rddj.info/) oder [RStudio Education](https://education.rstudio.com/blog/2020/05/remote-roundup/)) oder **[Python](https://www.python.org/)** (siehe dazu Ressourcen, wie [Data analysis with Python](https://csmastersuh.github.io/data_analysis_with_python_2020/ ) oder [Information Visualization](https://infovis.fh-potsdam.de/tutorials/)). 

Excel bietet jedoch mehr und einfachere Datenanalysemöglichkeiten, als man auf den ersten Blick vielleicht annehmen würde. Für diesen Kurs möchten wir Euch das einfache Tool **[PivotCharts und PivotTable](https://support.microsoft.com/de-de/office/%C3%BCbersicht-%C3%BCber-pivottables-und-pivotcharts-527c8fa3-02c0-445a-a2db-7794676bce96)** etwas näher bringen.

Wenn ihr Euch die eben importierten Daten anschaut, dann seht ihr, dass wir sie - um daraus Erkenntnisse zu gewinnen - im wesentlichen filtern und entsprechend summieren können müssen. PivotTable bietet dies sehr einfach, interaktiv und effizient. PivotCharts ist eine Ergänzung von PivotTables und erlaubt ebenfalls ein einfaches interaktives visualisieren der Daten. Damit können auf einfache Weise Muster erkannt und Vergleiche angestellt werden.


## Teil 3: Datawrapper

### Daten in Datawrapper laden

Datawrapper bietet einen Wizard an, um die Daten zu laden:

![Wizard von Datawrapper um Daten zu laden](https://user-images.githubusercontent.com/538415/102371585-9e790700-3fbe-11eb-966d-58f22547fd1c.png)
