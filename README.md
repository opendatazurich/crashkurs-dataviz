Einfache Datenanalyse und -visualisierung mit Excel und Datawrapper
==============================================

**Fragestellung: «Stimmt es, dass es in Zürich in den meisten Stadtquartieren mehr Hunde als Kleinkinder gibt?»**

Während dieses Kurses gehen wir dem Gerücht nach, ob in den meisten Stadtquartieren tatsächlich mehr Hunde als Kleinkinder leben. Wir werden mit Open Data die Fakten dazu checken und zeigen, wie wir die gewonnenen Erkenntnisse darstellen und sogar als interaktive Webgrafiken visualisieren können.

Damit wir diese Fragestellung einfach und mit für alle Kursteilnehmenden vorhandenen Tools beantworten können, haben wir uns für Excel und [Datawrapper](https://www.datawrapper.de/) entschieden. 

# Teil 1: Daten finden und beziehen
Zur Beantwortung der Fragestellung benötigen wir die dazu relevanten Daten. Wir müssen uns zuerst auf die Suche machen, wo wir die Anzahl Hunde und die Anzahl Kleinkinder pro Stadtquartier und Jahr beziehen können. Wie gut also, dass es in der Stadt Zürich einen [Open Data Katalog](https://data.stadt-zuerich.ch/) gibt, auf dem alle frei verfügbaren Verwaltungsdaten aufgelistet, ausführlich beschrieben und einfach durchsuchbar zum Download vorliegen ;)

- **Schritt 1:** Rufe den Open Data Katalog der Stadt Zürich auf unter: [https://data.stadt-zuerich.ch/](https://data.stadt-zuerich.ch/)
- **Schritt 2:** Suche nach Hundebestand pro Stadtquartier und Jahr. Gebe dazu im Suchfeld beispielsweise den Begriff «Hunde» und «Stadtquartier» ein. Beim Eintippen des Suchbegriffs werden bereits passende Vorschläge zu auf dem Katalog vorkommenden Daten angezeigt.  
<img src="https://user-images.githubusercontent.com/2479732/103986721-847caf80-518b-11eb-839c-95953ead6f67.png" alt="Suchresultatvorschau"/>

- **Schritt 3:** 
  - Wähle das Dataset «[Hundebestand der Stadt Zürich](https://data.stadt-zuerich.ch/dataset/sid_stapo_hundebestand)» aus und lies die Metadaten dazu. Besonders wichtig sind dabei die Attributbeschreibungen, welche die Ausprägungen der Informationen im Datensatz beschreiben. Hier sehen wir beispielsweise, dass es Angaben zu Hundehaltenden und Hunden gibt. Bereits in der ersten Attributbeschreibung zur technischen Identifikationsnummer der hundehaltenden Personen (`HALTER_ID`) erfahren wir eine sehr wichtige Information: ein Record (eine Zeile) im Datensatz entspricht einem Hund. Wenn demnach der gleiche Hundehaltende zwei Hunde hat, so kommt seine ID im Datensatz zweimal vor. Dank der Beschreibung können wir ebenfalls sicher sein, dass die Stadtquartiere in den Daten vorkommen. Weiterführende wichtige Informationen sind auch unter *Bemerkungen* zu finden. 
  - Die Datensätze selber sind unter *Daten und Ressourcen* zu finden. Wähle dort den aktuellsten Datensatz (2020) aus und klicke darauf. 
  - Dadurch öffnet sich eine neue Webseite, welche den Downloadlink und eine einfache Datenvorschau beinhaltet.
  - Klicke nun auf den Downloadlink, um die Daten herunter zu laden.
  <img src="https://user-images.githubusercontent.com/2479732/103988953-3669ab00-518f-11eb-99ab-0ca362d5cb0c.gif" alt="Dataset anschauen und Ressource downloaden" />
  
- **Schritt 4:** Suche nach einem Datensatz, der die Anzahl Kleinkinder pro Stadtquartier und Jahr beinhaltet. Da für die Definition eines Kleinkindes das Alter relevant ist, suchen wir also einen Datensatz, welcher das Alter der Bevölkerung nach Stadtquartier und Jahr beinhaltet. Gib daher im Suchfeld beispielsweise die Begriffe «Alter» und «Stadtquartier» ein. Als [Suchresultat](https://data.stadt-zuerich.ch/dataset?q=alter+stadtquartier&sort=score+desc%2C+date_last_modified+desc) erscheinen nun aber 35 Datensätze. Wir sollte daher noch einen besseren Begriff wählen. Verwende daher die Begriffe «Altersjahr» und «Stadtquartier», dadurch sind es nur noch 8 [Resultate](https://data.stadt-zuerich.ch/dataset?q=altersjahr+stadtquartier&sort=score+desc%2C+date_last_modified+desc).

- **Schritt 5:** Für unsere Fragestellung ist der Datensatz «[Bevölkerung nach Stadtquartier, Herkunft, Geschlecht und Alter, seit 1993](https://data.stadt-zuerich.ch/dataset/bev_bestand_jahr_quartier_alter_herkunft_geschlecht_od3903)» am geeignetsten. Er beinhaltet zwar mehr Informationen als wir benötigen (die Herkunft oder das Geschlecht interessieren uns eigentlich weniger), aber wir werden sie in einem späteren Schritt mit Excel herausfiltern.
 
- **Schritt 6:** Lies nun auch wieder die Metadaten zum Datensatz und gehe gleich wie in **Schritt 3** vor, um den Datensatz auf Deinen Computer herunter zu laden.

- **Schritt 7:** Du hast nun die beiden für unsere Fragestellung relevanten Datensätze gefunden und heruntergeladen. Sie heissen `20200306_hundehalter.csv` (Hunde) und `BEV390OD3903.csv`(Bevölkerungsdaten). Kopiere diese beiden Datensätze nun aus dem Downloadverzeichnis Deines Computers und lege sie in ein Verzeichnis, wo Du an den noch folgenden Schritten weiter arbeiten kannst. 

Damit ist unser erster Teil zum Thema «Daten finden und beziehen» beendet. Solltest Du später einmal für eine andere Fragestellung auf dem Open Data Katalog der Stadt Zürich nicht fündig werden, können auch viele andere Open Data Quellen konsultiert werden. Auf nationaler Ebene werden unter [opendata.swiss](https://opendata.swiss) sämtliche offenen Verwaltungsdaten von verschiedenen Bundesstellen, anderen Kantonen und Städten angeboten. 

# Teil 2: Excel

## CSV... what?
Eines der Grundprinzipien von Open Data ist, dass die Datensätze in **nicht-proprietären Formaten** veröffentlicht werden sollen. Sprich, für die Verwendung der Daten sollen die AnwenderInnen nicht auf kommerzielle Software angewiesen sein. Damit soll allen die gleiche Möglichkeit gegeben werden, mit den Daten arbeiten zu können. Das Excelformat (.xls oder .xlsx) ist ein Beispiel eines proprietären Datenformats, weil es zur Verwendung Excel erfordert.

Das Standardformat für tabellarische Daten ist daher [CSV](https://de.wikipedia.org/wiki/CSV_(Dateiformat)). CSV steht für **C**omma-**s**eparated **v**alues (komma-getrennte Werte).

**CSV-Beispiel:** 

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
Der angezeigte CSV-Auszug oben repräsentiert die folgende Tabelle:

![DarstellungExcel](https://user-images.githubusercontent.com/2479732/104014716-cc173180-51b3-11eb-9440-3d87d2fb6128.png)

## CSV-Datensätze in Excel laden

Vielleicht fragst Du Dich unterdessen, wozu der ganze Exkurs über CSV dienlich sein soll...(?) Leider ist es so, dass viele Datennutzende bereits zu diesem Zeitpunkt scheitern, wenn sie noch nie mit CSV gearbeitet haben und eine CSV-Datei in Excel öffnen wollen. Daher zeigen wir Euch in diesem Abschnitt, wie man vorgehen sollte, wenn man mit CSV-Datensätzen in Excel arbeiten möchte.

**Wie es NICHT funktioniert:**
Ein Doppelklicken auf eine CSV-Datei - wie in unten gezeigter Animation gezeigt - funktioniert leider in den meisten Fällen nicht. Obwohl man gemäss des im Beispiel angezeigten Icons der Datei das Gefühl hätte, dass dies so möglich sein sollte. Folgendes geschieht jedoch stattdessen: 

<img src="https://user-images.githubusercontent.com/2479732/104017881-32528300-51b9-11eb-8d15-39debf3c426a.gif" alt="ExcelFail" />

Die CSV-Datei wird zwar in Excel geöffnet, es findet dabei jedoch keine Trennung der einzelnen Attribute in Spalten statt (vgl. mit der oben gezeigten Tabelle). Mit der hier gezeigten Vorgehensweise sind alle Werte in eine Spalte (hier Spalte A) eingefügt worden. Damit lässt sich nicht bequem weiterarbeiten.

**Der Clou: CSV-Datei muss IMPORTIERT werden**

Damit ihr wie erwartet, basierend auf einem CSV-Datensatz, in Excel weiterarbeiten könnt, müsst ihr den CSV-Datensatz **importieren**. Dazu müsst ihr folgendermassen vorgehen:

- **Schritt 1:** Öffne eine neue leere Exceldatei und speichere Sie in Dein Verzeichnis, wo Du bereits die beiden CSV-Datensätze abgelegt hast ( `20200306_hundehalter.csv` und `BEV390OD3903.csv`). Gib dem Excelfile einen Namen, z.B. `Kleinkinder_und_Hunde.xlsx`.

- **Schritt 2:** Gehe zum Menu **Daten** und klicke auf **Externe Daten abrufen**. Wähle aus allen angezeigten Optionen **Aus Text** aus.

- **Schritt 3:** Mit dem Pop-Up **Textdatei importieren** wirst Du aufgefordert, die Textdatei auszuwählen, die Du nun ins Excelfile importieren möchtest. Wähle zuerst `20200306_hundehalter.csv` zum Import aus und klicke auf **Importieren**.

- **Schritt 4:** Nun erscheint das Pop-Up mit dem **Textkonvertierungs-Assistenten**, welcher dich durch drei Importschritte führt.
  - a) Wähle **Getrennt** aus, weil unsere Datensätze ja durch Kommas abgetrennt sind. Der Import beginnt in Zeile 1 und das CSV liegt in UTF-8 Kodierung vor. Aktiviere auch das Kästchen, dass die Datei Überschriften hat. Ganz unten siehst Du eine Vorschau, wie gemäss Deiner Auswahl der Import aussehen würde. Klicke nun auf **Weiter**.
  - b) Im nächsten Dialogfeld musst Du nun die Trennzeichen definieren. In unserem Fall, resp. bei CSV, sollte dies immer **Komma** sein. Wähle es aus und beobachte die Veränderung in der Vorschau. Wenn Du zufrieden bist, klicke auf **Weiter**.
  - c) Im letzten Dialogfeld kannst Du den Datentypen für jede Spalte definieren. Dies ist in den meisten Fällen nicht notwendig. In unserem Beispiel wurde noch explizit das Attribut Alter als Text definiert. Dies weil gewisse Werte von Excel z.T. auch als Datum interpretiert werden. Wenn Du zufrieden bist, klicke auf **Weiter**.  
  
- **Schritt 5:** Bestätige mit **OK** den Import in das aktuelle Arbeitsblatt Deines Excelfiles. Voilà, die Daten liegen nun so vor, dass Du mit den Hundedaten nun weiterarbeiten kannst.

<img src="https://user-images.githubusercontent.com/2479732/104021668-747ec300-51bf-11eb-859d-23aecceabee3.gif" alt="csvImport" />

- **Schritt 6:** Überschreibe unten links den Arbeitsblattnamen von *Tabelle 1* auf *Hundebestand_2020*. Dies erfolgt ganz einfach, indem Du auf den Text *Tabelle 1* doppelklickst und ihn dann überschreibst.

- **Schritt 7:** Füge nun - mit einem Klick auf das Plus-Zeichen - ein neues Arbeitsblatt hinzu und nenne es *Bevölkerungsbestand*.
- **Schritt 8:** Importiere nun `BEV390OD3903.csv`wie ab Schritt 3 beschrieben in unser Excelfile `Kleinkinder_und_Hunde.xlsx`. Tipp: definiere beim Import die Spalte *AlterV05Kurz* als Text, weil sonst einzelne Werte als Datum interpretiert und falsch dargestellt werden.

Damit sind wir fertig mit dem Datenimport. Unser Excelfile `Kleinkinder_und_Hunde.xlsx` beinhaltet nun zwei Arbeitsblätter mit den Hunde- und Bevölkerungsbestandsdaten, welche wir im nächsten Schritt analysieren werden.

<img src="https://user-images.githubusercontent.com/2479732/104026534-5a94ae80-51c6-11eb-8940-1b2ffcca7f3a.gif" alt="abschlussDatenImports" />

## Datenauswertung mit Excel 
Excel ist bezüglich Datenanalyse selbstverständlich nicht allererste Sahne. Fortgeschrittenere Datennutzende verwenden in der Regel eher Statistiktools wie **[R](https://www.r-project.org/)** (siehe dazu Ressourcen, wie [Rddj](https://rddj.info/) oder [RStudio Education](https://education.rstudio.com/blog/2020/05/remote-roundup/)) oder **[Python](https://www.python.org/)** (siehe dazu Ressourcen, wie [Data analysis with Python](https://csmastersuh.github.io/data_analysis_with_python_2020/ ) oder [Information Visualization](https://infovis.fh-potsdam.de/tutorials/)). 

Excel bietet jedoch mehr und einfachere Datenanalysemöglichkeiten, als man auf den ersten Blick vielleicht annehmen würde. Für diesen Kurs möchten wir Euch das einfache Excel-Tool **[PivotCharts und PivotTable](https://support.microsoft.com/de-de/office/%C3%BCbersicht-%C3%BCber-pivottables-und-pivotcharts-527c8fa3-02c0-445a-a2db-7794676bce96)** etwas näher bringen.

Wenn ihr Euch die eben importierten Daten anschaut, dann seht ihr, dass wir sie - um daraus Erkenntnisse zu gewinnen - im wesentlichen filtern und entsprechend summieren können müssen. PivotTable bietet diese Funktionalitäten sehr einfach, interaktiv und effizient an. PivotCharts ist eine Ergänzung von PivotTables und erlaubt ebenfalls ein einfaches interaktives visualisieren der Daten. Damit können auf einfache Weise Muster erkannt und Vergleiche angestellt werden.

### Anzahl Kleinkinder nach Stadtquartier
Beginnen wir zuerst einmal damit herauszufinden, wie viele Kleinkinder es pro Stadtquartier am 31.12.2019 gab.

- **Schritt 1:** Gehe zum Menu **Einfügen**, klicke aufs **PivotChart-Icon** und wähle **PivotChart und PivotTable**.

- **Schritt 2:** Mit dem Pop-Up **PivotTable erstellen** wirst Du aufgefordert, den Tabellenbereich der analysiert werden soll auszuwählen. Sofern Du alle Daten des aktiven Arbeitsblattes betrachten möchtest, musst Du hier nichts anpassen. Als weitere Option kannst Du auswählen, ob die PivotTable in ein bestimmtes oder in ein neues Arbeitsblatt eingefügt werden soll. Klicke danach auf **OK**.

- **Schritt 3:** Im neuen Arbeitsblatt erscheinen nun die noch leeren PivotTable- und PivotChart-Flächen. Auf der rechten Seite siehst Du die PivotTable-Felder, welche Du **interaktiv** per drag & drop in vier Bereiche ziehen kannst. 
  - a) **WERTE**: hier werden die zu aggregierenden Wertefelder definiert. In unserem Fall ist das die **Anzahl Personen** aus der wirtschaftlichen Wohnbevölkerung (`AnzBestWir`) .
  - b) **ZEILEN**: hier werden die Felder eingefügt, welche als Zeilen dargestellt werden sollen. In unserem Fall also die **Stadtquartiere** (`QuartLang`). Die Stadtquartiere können mit ihren Namen oder mit ihren offiziellen IDs (`QuartSort`oder `QuartCd`) angezeigt werden.
  - c) **SPALTEN**: hier könnten weitere Ausprägungen ausgewählt werden, wie z.B. das Geschlecht oder die Herkunft. Für unsere Fragestellung sind diese Felder jedoch nicht relevant. Deshalb bleibt dieser Bereich leer.
  - d) **FILTER**: hier können für Attribute gewisse Werte aus den Daten gefiltert werden. So müssen wir nun das für uns relevante **Jahr** (`StichtagDatJahr`), also **2019**, auswählen. Ausserdem betrachten wir ja lediglich die Kleinkinder. Wir definieren sie hier als jene Personen in der **Alterskategorie** (`AlterV05Kurz`) **0-4**. Also der Kinder die jünger als 5 Jahre alt sind. Man könnte die Definition selbstverständlich auch anders festlegen.
  
- **Schritt 4:** Damit haben wir nun bereits die erforderliche Tabelle und eine simple Grafik der Anzahl Kleinkinder pro Stadtquartier Ende 2019. Benenne das Arbeitsblatt wieder, z.B. mit `BevBest_Pivot`.

<img src="https://user-images.githubusercontent.com/2479732/104037207-ac443580-51d4-11eb-8458-4ee22822d42d.gif" alt="BevBest_Pivot"/>

### Anzahl Hunde nach Stadtquartier
Als nächstes gehen wir analog der vorherigen Schritte vor und analysieren nun, wie viele Hunde es pro Stadtquartier Anfangs März 2020 gab.

- **Schritt 1:** Wechsle ins Arbeitsblatt **Hundebestand_2020** und gehe erneut zum Menu **Einfügen**, klicke aufs **PivotChart-Icon** und wähle **PivotChart und PivotTable**.
- **Schritt 2:** Mit dem Pop-Up **PivotTable erstellen** wirst Du wieder aufgefordert, den Tabellenbereich der analysiert werden soll auszuwählen. Dieses Mal sollte sich die Tabelle auf die pivotiert wird selbstverständlich auf den Hundebestand 2020 beziehen. Klicke danach auf **OK**.

- **Schritt 3:** Im neuen Arbeitsblatt erscheinen erneut die leeren PivotTable- und PivotChart-Flächen. Auf der rechten Seite siehst Du nun die PivotTable-Felder aus dem aktuellen Datensatz des Hundebestands, welche Du wieder in die vier Bereiche ziehen kannst. 
  - a) **WERTE**: hier werden die zu aggregierenden Wertefelder definiert. Dieses Mal gilt es zu beachten, dass wir kein Feld wie *Anzahl Hunde* oder ähnliches vorfinden. Dies liegt daran, dass jede Zeile in den Daten einem Hund entspricht. Die **Anzahl Hunde** finden wir jedoch heraus, indem wir das Attribut Halter-ID (`HALTER_ID`) auswählen und in der **Wertfeldeinstellung** (rechte Maustaste auf *Summe von HALTER_ID*) von Wertfeld zusammenfassen als Summe auf **Anzahl** wechseln. Die mit der Option Summe würden alle HALTER_IDs summiert werden, was ja keinen Sinn macht.
  - b) **ZEILEN**: Dieses Mal kommen lediglich numerische Werte für die Stadtquartiere vor. Wir wählen hier daher die Stadtquartier-IDs (`STADTQUARTIER`) aus. 
  - c) **SPALTEN**: auch hier könnten weitere Ausprägungen ausgewählt werden, wie z.B. die Rasse, die Farbe, das Geburtsjahr oder das Geschlecht des Hundes. Für unsere Fragestellung sind diese Attribute jedoch nicht relevant. Deshalb bleibt dieser Bereich leer.
  - d) **FILTER**: eine Filtervariable benötigen wir dieses Mal nicht, weil sich die Daten ja lediglich auf ein Jahr beziehen. Eine weitere Ausscheidung von Attributwerten ist auch nicht notwendig. Dehalb bleibt dieser Bereich auch leer.

<img src="https://user-images.githubusercontent.com/2479732/104046181-f8e13e00-51df-11eb-8c74-4f3e15db1f8f.gif" alt="HundeBest_Pivot"/>

- **Schritt 4:** Damit haben wir nun die Anzahl Hunde pro Stadtquartier als Tabelle. Benenne das Arbeitsblatt wieder, z.B. mit `HundeBest2020_Pivot`.

### Vergleich zur Anzahl Hunde und Kleinkinder
Damit wir die Resultate der Anzahl Hunde und Anzahl Kleinkinder pro Stadtquartier vergleichen können, kopieren wir am einfachsten die Resultate der Pivot-Tabellen in ein neues Arbeitsblatt.

- **Schritt 1:** Füge ein neues Arbeitsblatt (mit Klick auf das Plus-Zeichen unten rechts neben den anderen Arbeitsblättern) hinzu. Gib ihm einen Namen. In unserem Beispiel `Vgl_Kleinkinder_Hunde`.

- **Schritt 2:** Kopiere die Werte der Anzahl Kleinkinder pro Stadtquartier und füge sie ins neue Arbeitsblatt ein. 

- **Schritt 3:** Mache das gleiche mit den Werten zur Anzahl Hunde pro Stadtquartier und füge sie mit etwas Abstand rechts ins neue Arbeitsblatt ein. 

<img src="https://user-images.githubusercontent.com/2479732/104167948-86e64000-53fd-11eb-9a1a-152601170a01.gif" alt="VergleicheResultate"/>

- **Schritt 4:** Wir haben nun das Problem, dass bei den Kleinkindern die Namen und bei den Hunden die IDs der Stadtquartiere angegeben sind. So lassen sich die Werte nicht vergleichen. Daher braucht es hier noch einen Zwischenschritt, in dem wir eine **Zuordungstabelle** von Stadtquartier-IDs zu den -Namen machen.

  - a) Im Arbeitsblatt `Bevölkerungsbestand` kommen sowohl die Quartiernummer als auch der Quartiernamen vor. Erstelle daher in diesem Arbeitsblatt eine neue PivotTable.
  
  - b) Wähle das Feld `QuarSort` und ziehe es ins Feld **WERTE**. 
  
  - c) Wähle das Feld `QuarLang` und ziehe es ins Feld **ACHSE**. 
  
  - d) Wir wollen nicht die Summe der Quartiernummern, sondern die minimalen Werte wissen. Wähle daher mit rechte Maustaste auf *Summe von QuarSort* und wechsle über die Wertfeldeinstellungen von Wertfeld zusammenfassen als Summe auf **Minimum**.  
   
  - e) Damit ist die Zuordnungstabelle erstellt. Jede Stadtquartier-ID hat nun einen entsprechenden Stadtquartiernamen.
   
- **Schritt 5:** Kopiere die Zuordnungstabelle ins Arbeitsblatt `Vgl_Kleinkinder_Hunde`.

- **Schritt 6:** Sortiere nun (Menu Daten > Sortieren) wie in der Grafik angezeigt zuerst die Werte der Anzahl Kleinkinder nach der Quartiernummer nach Grösse aufsteigend. Vergleiche ob die Quartiernummern mit jenen der Anzahl Hunde, ebenfalls nach Grösse aufsteigend sortiert, entspricht. Lösche danach die doppelt vorhandenen Spalten und reihe die Attibute nach Deinem Gusto aneinander.

<img src="https://user-images.githubusercontent.com/2479732/104171823-8badf280-5403-11eb-9dce-42cb5e4f97f9.gif" alt="Zuordnungstabelle_Sort"/>


- **Schritt 7:** Berechne in in einer neuen Spalte - im Beispiel namens Diff_Kkinder-Hunde - die Differenz zwischen der Anzahl Kleinkinder und der Anzahl Hunden. Berechne den Wert in der obersten Spalte mit der Formel '=D2 - C2' und ziehe den Punkt unten rechts im grünen Rechteck für alle Quartiere herunter. Die Formel wird so überall korrekt übernommen.

- **Schritt 8:** Sortiere die Differenzen (Spalte E) aufsteigend. Das Resultat ist nun als Tabelle ersichtlich.

- **Schritt 9:** Stelle das Resultat mit PivotChart als Balkendiagramm dar:

  - a) Füge den Quartiernamen im Feld **ACHSE** und die Differenzwerte im Feld **WERTE** ein.
  - b) Sortiere absteigend nach den Differenzwerten. Klicke dazu in der PivotTable auf das Dropdownzeichen rechts neben *Zeilenbeschriftung*. Klicke auf *Weitere Sortieroptionen*, wähle *Absteigend* und wähle die Differenzwerte aus.

- **Schritt 10:** Ändere den Diagrammtyp auf Balkendiagramm. Klicke mit der rechten Maustaste auf den PivotChart > wähle *Diagrammtyp ändern* > wähle *Balken* > dann *Gruppierte Balken* aus. Layoute das Balkendiagramm (Titel, Höhe, Breite, Farbfüllung, etc.)

- **Schritt 10:** Falls Dir die Grafik noch zu umfangreich ist, kannst Du auch einzelne Bereiche herausfiltern. Gehe dazu wieder wie in Schritt 9b) vor und wähle dieses Mal *Wertefilter* aus. In der Animation werden z.B. nur jene Stadtquartiere angezeigt, wo die Differenz zwischen Kleinkindern und Hunden kleiner als 50 ist. Alle anderen Werte werden nicht angezeigt.
  
<img src="https://user-images.githubusercontent.com/2479732/104203191-26222c00-542c-11eb-8e0a-4c3016d04406.gif" alt="DiagrammErstellen"/>


## Überrascht vom Resultat?
Nun haben wir also Gewissheit: Ende 2019 lebten nur im Stadtquartier **Lindenhof** (Bevölkerungszahl 2019: 1'009) im Kreis 1 mehr Hunde (27) als Kleinkinder (22). Bei allen Stadtquartieren im Kreis 1 war die Differenz zwischen Kleinkindern und Hunden relativ klein.
Am grössten ist die Differenz hingegen in den bevölkerungsreichsten Stadtquartieren Altstetten (mit +1'133) und Affoltern (+1'115).

# Teil 3: Datawrapper
Für dieses Kurs verwenden wir das kostenlose Tool [Datawrapper](https://www.datawrapper.de/), welches [ohne Login ausprobiert werden kann](https://app.datawrapper.de/chart/create).
Es wird bereits von vielen Datenjournalisten eingesetzt, da es sehr benutzerfreundlich ist und sich damit ohne eigenen Code zu schreiben Visualisierungen fürs Web erstellen lassen.

Datawrapper steht hier stellvertretend für viele andere Tools, die einen ähnlichen Funktionsumfang bieten:

* [Tableau](https://www.tableau.com/)
* [Microsoft Power BI](https://powerbi.microsoft.com/de-de/)
* [Google Charts](https://developers.google.com/chart)
* [Plotly](https://plotly.com/)

## Daten vorbereiten
Wie wir in [Teil 2](#teil-2-excel) gesehen haben, müssen Daten zuerst in eine Form gebracht werden, in der sie visualisiert werden können.
In diesem Schritt arbeiten wir also wieder mit der Excel-Datei aus dem letzten Teil.
Es steht auch eine [Beispiel-Exceldatei zur Verfügung](https://github.com/opendatazurich/crashkurs-dataviz/raw/main/files/daten_excel_crashkurs.zip) (inkl. den _verlinkten_ CSVs).

## Hunde nach Stadtquartier und Geschlecht
Als Abschluss möchten wir noch eine interaktive Grafik erstellen basierend auf dem Hundebestand.
Dazu müssen wir eine neue Pivot-Tabelle erstellen, mit der wir die Werte für die Grafik aggregieren können:

- **Schritt 1:** Wechsle ins Arbeitsblatt `Hundebestand_2020` und gehe zum Menu **Einfügen**, klicke auf **PivotTable**.
- **Schritt 2:** Mit dem Pop-Up **PivotTable erstellen** wirst Du wieder aufgefordert, den Tabellenbereich der analysiert werden soll auszuwählen. Dieses Mal sollte sich die Tabelle auf die pivotiert wird selbstverständlich auf den Hundebestand 2020 beziehen. Klicke danach auf **OK**.
- **Schritt 3:** Im neuen Arbeitsblatt erscheinen nun die noch leeren PivotTable-Flächen. Erstelle eine Pivot-Tabelle mit folgenden Angaben:
  - a) **WERTE**: Anzahl Halter-ID (`HALTER_ID`) auswählen und in der **Wertfeldeinstellung** (rechte Maustaste auf *Summe von HALTER_ID*) von Wertfeld zusammenfassen als Summe auf **Anzahl** wechseln.
  - b) **ZEILEN**: Stadtquartier-IDs (`STADTQUARTIER`)
  - c) **SPALTEN**: Geschlecht des Hundes (`GESCHLECHT_HUND`)
  
![Pivot-Tabelle für Hunde nach Stadtquartier und Geschlecht](https://user-images.githubusercontent.com/538415/104384802-5eac2d80-5532-11eb-906d-8d5836cee961.png)

- **Schritt 4:** Kopiere die Werte der Anzahl Hund pro Stadtquartier und Geschlecht und füge sie in ein neues Arbeitsblatt ein.
- **Schritt 5:** Kopiere die Zuordnungstabelle ([siehe weiter oben](#vergleich-zur-anzahl-hunde-und-kleinkinder) zwischen Quartiernamen und -nummern ebenfalls in dieses neue Arbeitsblatt ein
- **Schritt 6:** Benenne die Spalten und Tabellenblätter aussagekräftig, z.B. männlich, weiblich und Quartier

![Zuordnungstabelle hinzufügen](https://user-images.githubusercontent.com/538415/104387735-0a0bb100-5538-11eb-892d-a17ef0b0d17c.gif)

### Daten in Datawrapper laden
Um die Daten von Excel zu Datawrapper zu importieren, kann der [Wizard von Datawrapper](https://app.datawrapper.de/chart/create) verwendet werden.

![Wizard von Datawrapper um Daten zu laden](https://user-images.githubusercontent.com/538415/102371585-9e790700-3fbe-11eb-966d-58f22547fd1c.png)

- **Schritt 1:** In Excel die Tabelle kopieren und bei Datawrapper im Textfeld wieder eingefügt werden.
- **Schritt 2:** Klick auf **Weiter** und anschliessend die Daten überprüfen (Sind alle Spalten da? Wurden die Datentypen richtig erkannt?)
- **Schritt 3:** Um männlich/weiblich als Kategorien zu nutzen für jedes Quartier, sollte die Tabelle noch transponiert werden (Spalten und Zeilen vertauschen)

![Daten zu Datawrapper kopieren](https://user-images.githubusercontent.com/538415/104389217-3ffe6480-553b-11eb-8b28-3d5041e2565a.gif)

### Diagramm erstellen
Im letzten Schritt geht es jetzt noch darum, das Diagramm zu definieren.
Die vorliegenden Daten zeigen pro Quartier die Anzahl weibliche und die Anzahl männliche Hunde.
Es liegt daher nahe ein gestapeltes Säulendiagramm zu erstellen, da ein Balken pro Quartier für alle Hunde steht und dieser nach Geschlecht aufgeteilt ist.

![Diagramm anpassen](https://user-images.githubusercontent.com/538415/104390094-35dd6580-553d-11eb-9eef-a77456092750.gif)

### Resultat
Voilà, hier das Resultat (ein Klick auf das Bild öffnet die interaktive Grafik):

[![Diagramm von Datawrapper](https://user-images.githubusercontent.com/538415/104390214-750bb680-553d-11eb-85b5-bb2fbe5e88e4.png)](https://datawrapper.dwcdn.net/FWDgZ/1/)

## Kleinkinder-Hunde Koeffizient
Im späteren Verlauf möchten wir das Verhältnis zwischen Kleinkindern und Hunden auf einer Karte der Stadt Zürich darstellen.
Dazu werden wir eine sogenannte [Choroplethenkarte (Flächenkartogramm)](https://de.wikipedia.org/wiki/Choroplethenkarte) erstellen.
Auf solchen thematischen Karten wird das Verhältnis einer Grösse zum Gebiet dargestellt (z.B. Bevölkerungsdichte).

Aus diesem Grund fügen wir im Excel auf dem bestehenden Arbeitsblatt `Vgl_Kleinkinder_Hunde` eine weitere Spalte hinzu.

- **Schritt 1:** Gehe zum Arbeitsblatt `Vgl_Kleinkinder_Hunde`.
- **Schritt 2:** Füge eine neue Spalte KleinkinderHundeKoeffizient hinzu
- **Schritt 3:** Berechne in dieser neuen Spalte das Verhältnis zwischen der Anzahl Kleinkinder und der Anzahl Hunden. Berechne den Wert in der obersten Spalte mit der Formel '=D2 / C2' und ziehe den Punkt unten rechts im grünen Rechteck für alle Quartiere herunter. Die Formel wird so überall korrekt übernommen.

### Choroplethenkarte erstellen
Neben den Diagrammen, können mit Datawrapper auch [einfache Karten erstellt](https://app.datawrapper.de/create/map) werden.

- **Schritt 1:** Gehen zum Datawrapper Wizard und wähle **Neue Karte** -> **Choroplethen-Karte**
- **Schritt 2:** Suche nach "Zürich Quartier" und wähle die Standardkarte **Schweiz » Zürich » Stadtquartiere**
![Karte auswählen](https://user-images.githubusercontent.com/538415/104391079-6aeab780-553f-11eb-84d8-06103ecf3a60.png)
- **Schritt 3:** Klicke auf **Weiter** und wähle **Codes** als Geo-Code
- **Schritt 3:** Klicke auf **Importiere deinen Datensatz** und kopiere die Tabelle vom Arbeitsblatt `Vgl_Kleinkinder_Hunde`, die du dann anschliessend in Datawrapper einfügen kannst
- **Schritt 4:** Wähle die Spalte `Quartiernummer` als Code-Spalte und die Spalte `KleinkinderHundeKoeffizient` als Wert-Spalte

Anschliessend können noch Anpassungen an der Karte vorgenommen werden wie z.B. das verändern der Farbskala oder das einzigen der Quartiernamen anstatt der Codes.

### Resultat

Voilà, hier das Resultat (ein Klick auf das Bild öffnet die interaktive Karte):
[![Choroplethen-Karte](https://user-images.githubusercontent.com/538415/104439523-79fa5580-5591-11eb-8d91-8946e0d3954d.png)](https://datawrapper.dwcdn.net/dq1wu/1/)

# Anhänge
## Excel-Datei
Die Excel-Datei, auf der dieser Kurs basiert, kann von GitHub heruntergeladen werden: [ZIP-Datei mit den verlinkten CSVs](https://github.com/opendatazurich/crashkurs-dataviz/raw/main/files/daten_excel_crashkurs.zip).
[![Excel-Datei](https://user-images.githubusercontent.com/538415/104441265-bb8c0000-5593-11eb-91ac-daf61d617bc1.png)](ttps://github.com/opendatazurich/crashkurs-dataviz/raw/main/files/daten_excel_crashkurs.zip)

Beim Öffnen wird Excel eine Warnung anzeigen, dass die Datei repariert werden muss.
Dies liegt daran, dass der Pfad zu den CSV-Dateien nicht gefunden wird.
Der Fehler kann ignoriert werden für diesen Kurs.

## Tutorials
### Datawrapper
Datawrapper hat eine Reihe von [Tutorials](https://academy.datawrapper.de/) und [Schulungsunterlagen](https://www.datawrapper.de/training-materials/), die die einzelnen Diagramm- und Karten-Typen erklären und wie damit Visualisierungen erstellt werden können.

Beispiele:

- [Let’s build a stacked bar chart](https://www.datawrapper.de/training-materials/#exercise-1)
- [How to create a grouped column chart](https://academy.datawrapper.de/article/21-how-to-create-a-grouped-column-chart)
- [How to choose the best interpolation for your colors (choropleth map)](https://academy.datawrapper.de/article/117-color-palette-for-your-map)

### Programmierung (R, Python, SPARQL)
- [Data analysis with Python](https://csmastersuh.github.io/data_analysis_with_python_2020/)
- [Information Visualization](https://infovis.fh-potsdam.de/tutorials/).
- [Einführung in Wikidata](https://www.wikidata.org/wiki/Wikidata:Tours), siehe dazu auch das [Trainingsmaterial von Open Data Zürich zu Wikidata](https://github.com/opendatazurich/wikidata-training).
- Jupyter Notebooks von Open Data Zürich zu
  - [Geoportal](https://github.com/opendatazurich/opendatazurich.github.io/blob/master/geoportal/Geoportal-Beispiele.ipynb)
  - [Luftqualitätsmessungen](https://github.com/opendatazurich/quality-checks/blob/master/luftqualitaet/Luftschadstoffdaten%20(1983%20bis%20heute).ipynb)
  - [Visualisierung von CSV mit Python/matplotlib](https://github.com/opendatazurich/opendatazurich.github.io/blob/master/csv/CSV%20mit%20Python%20verarbeiten%20(matplotlib).ipynb)
  - [Zürich Tourismus API](https://github.com/opendatazurich/opendatazurich.github.io/blob/master/zt-api/ZuerichTourismusAPI-Beispiele.ipynb)
