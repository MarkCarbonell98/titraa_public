# TeXnicCenter
Created Mittwoch 20 Juli 2016


AM BESTEN NICHT VERWENDEN!!!!!!! TEXSTUDIO IST VIEL BESSER UND EINFACHER
------------------------------------------------------------------------
Benutzung auf eigene Gefahr.

Installation
------------


1. Miktex pfad:

	C:\Users\sandro\AppData\Local\Programs\MiKTeX 2.9\miktex\bin
	C:\Program Files (x86)\MiKTeX 2.9


![](./TeXnicCenter/pasted_image.png)

	C:\Program Files (x86)\gs\gs9.19\bin/gswin32.exe

Die restlichen Felder freilassen.


![](./TeXnicCenter/pasted_image001.png)
	C:\Program Files\SumatraPDF\SumatraPDF.exe



4. auf fertigstellen klicken



IIIT Miktex package hinzufügen
------------------------------


Vorwärts und Rückwärtssuche einrichten - Summatra PDF konfigurieren
-------------------------------------------------------------------
In TeXnicCenter zu Ausgabe → Ausgabeprofilbearbeiten navigieren
![](./TeXnicCenter/pasted_image002.png)


* Den Tab **Nachbearbeitung **auswählen.
* den Eintrage **Latex ⇒ PS ⇒ PDF ** mit der Schaltfläche kopieren duplizieren. Anschließend den neuen Eintrag auswählen.
* im Tab Nachbearbung **ps2pdf **auswählen
* Programm und Argument anpassen

	Programm = Pfad zu ghostscript
	
	C:\Program Files (x86)\gs\gs9.19\bin/gswin32.exe
	
	Argumente
	
	-sPAPERSIZE=a4 -dSAFER -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile="%bm.pdf" -c save pop -f "%bm.ps" 


* Jetzt den Tab **Viewer** auswählen



### Testen
Im TeXnicCenter wie gewohnt auf Ausgabe erstellen(F7) drücken. Im PDF (mit Summatra PDF geöffnet)
kann dann einfach durch Doppelklick in die entsprechende Zeile im Latexcode gesprungen werden.
**Die Suche funktioniert auch, wenn Latex - PDF complierung ausgewählt wurde**

Projekt anlegen in TeXnicCenter
-------------------------------


Einfach die Dateien hinzufügen. Dann die **diplom.tex** auswählen und dann Projekt ⇒ Erzeugen mit aktueller Datei als Hauptdatei.
![](./TeXnicCenter/pasted_image003.png)



FAQ
---
Manchmal behebt ein umstellen auf Latex => PDF fehler







