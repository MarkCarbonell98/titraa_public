# Zotero
Created Mittwoch 20 Juli 2016


Zotero
------
<https://www.zotero.org/>

### Einleitende Worte

* cross platform
* plugin support
* kostenlose synchronisation (solange weniger als 100mb Dateien)
* firefox plugin, um die datei direkt aus dem browser in zotero zu speichern. Es gibt auch ein chrome plugin, das aber bisher noch nicht so gut ist (stand Juli 2016)


### Zotero Kurse in der BIB
<http://www.bibliothek.kit.edu/cms/veranstaltungskalender.php/event/31282>


Installation und Einrichtung
----------------------------

### Windows

1. auf diese Seite gehen: <https://www.zotero.org/download/>

![](./Zotero/pasted_image.png)

2. Download Zotero for Windows
3. Installation von Zotero
4. Zotero starten. Es wird gefragt, ob die open office plugins installiert werden sollen. Ist eigentlich egal, obs mans macht. Wenns mans installiert sollte man JRE (Java Runtime Environment) installiert haben. (google JRE)
5. Den Standardspeicherpfad von Zotero ändern.
	a. Es ist emfehlenswert, den Speicherpfad in einen Dropbox/Googledrive ordner zu ändern.
		1. Wenn der Rechner kaputt geht kann man ganz einfach alle Quellen wiederherstellen, in dem man bei einer neuen Installation von Zotero den Pfad wieder ändert
		2. Für Multiboot systeme ebenfalls sehr gut, da man Zotero auf beiden Systemen aus dem Ordner laufen lassen kann
		3. Man kann am Institutsrechner und von daheim arbeiten, weil alles durch die dropbox synchronisiert wird ⇒ kein Zotero sync notwendig.
	b. Gehe zu Werkzeuge ⇒ Einstellungen ⇒ Reiter "Erweitert" ⇒ Tab "Dateien und Ordner" ⇒ Speicherort ⇒ Eigene

![](./Zotero/pasted_image001.png) 

c. Ändere den Speicherort in einen Ordner deiner Wahl (Dropbox/GoogleDrive)

![](./Zotero/pasted_image002.png)


6. Zotero wird einen Neustart verlangen. Danach solltest du alle bereits angelegten Einträge sehen (falls du welche hast, falls nicht natürlich nicht).

![](./Zotero/pasted_image003.png)


### Windows & Linux - Better Bibtex Plugin
Dieses Plugin ist umbedingt notwendig, um sinnvoll zu arbeiten

#### Links
<https://github.com/retorquere/zotero-better-bibtex>
Installation (wirklich sehr kurzer prozess, daher hier keine hinweise) :
<https://github.com/retorquere/zotero-better-bibtex/wiki/Installation>
download link for latest release:
<https://github.com/retorquere/zotero-better-bibtex/releases/tag/1.6.89>
lade die **.xpi** Datei herunter

List of citation keys:
<https://github.com/retorquere/zotero-better-bibtex/wiki/Citation-Keys>


#### Installation
download link for latest release:
<https://github.com/retorquere/zotero-better-bibtex/releases/tag/1.6.89>
Dann weiter wie auf der Installationsseite:

![](./Zotero/pasted_image004.png)


Nach der Installation können die Einstellungen angesehen werden durch:

1. *Werkzeuge* ⇒ *Einstellungen* ⇒ *BetterBibTex* . BZW: Bearbeiten ⇒ Einstellungen ⇒ Better Bib Tex. Sinnvolle Einstellungen sind:
	a. *Automatic expor*t ⇒ *On Change*   | Dadurch werden neue Quellen sofort exportiert. Ist besser fürs schreiben der Arbeit
	b. *Export* ⇒ *Export subcollections* ⇒ ankreuzen.  | Dadurch können die Quellen besser sortiert werden.
	c. *Export* ⇒ *Add URLs to BibTeX export* ⇒ select *in an url field*





### Firefox Plugin
Das Firefox plugin ist extrem empfehlenswert. 
<https://www.zotero.org/download/>

Auch in Firefox sollte der Ordner gleich eingestellt werden wie in Zotero. Daher bei der folgenden Meldung **JA** drücken.

![](./Zotero/pasted_image023.png)



Einen Eintrag zu Zotero hinzufügen
----------------------------------

### Über das Firefox Plugin

1. Zotero öffnen
2. in Zotero die entsprechende Sammlung auswählen. Für dieses Beispiel wird "TiTrAa" ausgewählt.

![](./Zotero/pasted_image008.png)

3. Auf diesen Link gehen:  <http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=821744&tag=1>
4. oben rechts in Firefox auf den Pfeil nach unten beim Zotero plugin drücken und folgende Aktion auswählen

![](./Zotero/pasted_image009.png)

5. In Zotero befindet sich nun der BibTex Eintrag, die "Full Text" PDF-Datei und ein Schnappschuss der Webseite (html) 
	a. __Das PDF gibts nur wenn man im KIT netz st.__
	b. Den Bibtex eintrag bekommt man immer.

![](./Zotero/pasted_image010.png)
	

### Durch Drag & Drop einer PDF Datei

1. Zum Beispiel diese PDF Dateien herunterladen und IRGENDWO speichern:

<http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5470842>
<https://www.cs.toronto.edu/~hinton/absps/fastnc.pdf>
(Für die Anleitugn werden beide benötigt)

3. Die Dateien mit Drag & Drop auf die Sammlung ziehen (im Bild ist nur eine Datei gezeigt).

![](./Zotero/pasted_image011.png)

3. Die Datei ist nun als PDF in der sammlung, aber ohne BibTex Eintrag (im Bild ist nur eine Datei gezeigt). Daher muss dieser noch hinzugefügt werden. Dafür gibt es zwei Möglichkeiten.

![](./Zotero/pasted_image012.png)

#### BibTex eintrag nachträglich automatisch hinzufügen
Ausgehend von (3.) (im Bild ist nur eine Datei gezeigt)

![](./Zotero/pasted_image012.png)



4. Rechtsklick auf Datei ⇒ Rufe Metadataen für PDF-Datei ab

![](./Zotero/pasted_image013.png)

5. Klappt oft, aber nicht immer. Wenns nicht klappt muss man den Bibtex eintrag manuell hinzufügen (siehe nächsten Eintrag)

![](./Zotero/pasted_image015.png)
![](./Zotero/pasted_image014.png)


#### BibTex eintrag nachträglich manuell hinzufügen
Ausgehend von (3.) (im Bild ist nur eine Datei gezeigt)

![](./Zotero/pasted_image012.png)


4. Google suche nach dem Bibtex Eintrag ⇒ Titel der Arbeit + "BibTeX"
5. Man sollte nach etwas derartigem suchen:

<http://dl.acm.org/citation.cfm?id=1161605>
![](./Zotero/pasted_image017.png)
	
![](./Zotero/pasted_image016.png)

6. Den Bibtex eintrag im Browser markieren und kopieren (CTRL+C)
7. in Zotero: 

Datei ⇒ Import aus Zwischenablage
![](./Zotero/pasted_image018.png)

8. Der Bibtex Eintrag ist nun vorhanden

![](./Zotero/pasted_image019.png) 
 9. Für eine bessere Ordnung sollte man das PDF mit Drag & Drop in den Bib-Tex eintrag verschieben
![](./Zotero/pasted_image020.png)
	
![](./Zotero/pasted_image021.png)


10. fertig



### Eintrag überprüfen und korrigieren
<http://www.ece.ucdavis.edu/~jowens/biberrors.html>
wie schon erwähnt müssen die Eintrage überprüft werden, auch wenn sie von IEEE direkt importiert werden.

![](./Zotero/pasted_image022.png)

* hier ist Beispielsweise der Titel nicht gleich geschrieben (Anfangsbuchstaben sind groß)




Bibliothek zu Bibtex exportieren
--------------------------------

1. Auswahl einer Sammlung (Beispiel "Bachelorarbeit"). Es werden alle Unterbibliotheken mitexportiert.
2. Rechtsklick ⇒ Sammlung Exportieren

![](./Zotero/pasted_image006.png)

3. Format UNBEDINGT Better BibTex wählen (sofern BibTex gewünscht ist)
4. Notizen NICHT exportieren
5. Keep updated ⇒ yes


3. Speicherort auswählen. Es bietet sich an, die Datei in "diplom.bib" in der Latexvorlage zu überschreiben.
4. fertig


Der Export kann nun in den Einstellungen von Better Bib Tex gesehen werden. Nach Bedarf kann dort auch ein export erzwungen werden (export), um die die .bib Datei zu aktualisieren.
![](./Zotero/pasted_image007.png)


