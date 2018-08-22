# 03 01 01 mitInkscape
Created Samstag 04 Februar 2017

Erstellen von Skizzen ...
-------------------------
Auch bei Skizzen sollte das Dateiformat svg oder pdf angestrebt werden. Schön ist natürlich, wenn man Latex-Schriftarten hinbekommt.

### ... mit Inkscape
Unterstützt EPS-Latex ⇒ Latexschriften möglich


1. Den Arbeitsbereich auf die Breite 16cm begrenzen. Die Höhe kann maximal 22cm betragen

File ⇒ Document Properties ⇒ Costum size ⇒ Width = 16cm, Höhe maximal 22cm ⇒ Fenster schließen

2. **Aufgrund eines komischen Bugs** muss man für ein korrektes verhalten ein **weißes Rechteck** komplett über die Zeichenfläche ziehen. (Stand Sept. 16)

In manchen Fällen hat auch ein transparentes Rechteck funktioniert

a. Rechteck über die gesamte Zeichenfläche legen

 ![](./03_01_01_mitInkscape/pasted_image018.png)

b. Object in den Hintergrund verschieben: Object ⇒ Lower to Bottom (shortcut END)

![](./03_01_01_mitInkscape/pasted_image019.png)

c. Object weiß machen. Dazu das entsprechende Icon in der rechten Seitenleiste auswählen oder **Objekte ⇒ Füllung und Kontur** 
	1. und oder die Farbe weiß machen [R=G=B=255] und den Rahmen löschen

 ![](./03_01_01_mitInkscape/pasted_image017.png)
![](./03_01_01_mitInkscape/pasted_image020.png)
		

3. Wie gewohnt eine Skizze in Inkscape erstellen
	a. beim erstellen von Textfeldern die Schriftgröße zu 10 ändern

![](./03_01_01_mitInkscape/pasted_image014.png)

b. Für Mathematik muss $$ verwendet werden. Es können die Befehle aus der Latexvorlage verwendet werden.


4. . Am Ende Speichern Unter ⇒ EPS auswählen

![](./03_01_01_mitInkscape/pasted_image015.png)

5. EPS_tex aktivieren

![](./03_01_01_mitInkscape/pasted_image016.png)

6. Einbinden genauso wie PDF_tex (Pfad in eps_tex Datei beachten)
	a. in der eps_tex Datei wird wieder **\includegraphics **benutzt. Daher ist der Pfad hier relativ zum Stammordner für bilder. 

In der Latexvorlage ist dieser Standardmäßig in der Datei **Erweiterungen.tex **zum Ordner "bilder" gewählt. Daher muss er in der __.eps_tex Datei nicht angegeben werden.
Beim einbinden in das Latexdokument wird allerdings der Pfad relativ zum document root benötigt.
	%% code für die ausarbeitung
	
	\begin{figure}[h!]
	  \centering
	  \def\svgwidth{\textwidth}
	    \input{bilder/drawings/EPS_drawing_Inkscape.eps_tex}
	  \caption{Matlab - Plot2Latex - pdftex Datei einbinden}
	\end{figure}
		
Pfad in der ___.eps_tex datei
![](./03_01_01_mitInkscape/pasted_image023.png)


#### Ergebnis
![](./03_01_01_mitInkscape/pasted_image021.png) ![](./03_01_01_mitInkscape/pasted_image024.png)
Links: Zeichnung in Inkscape  ----  Rechts: Eingebundene Datei in LATEX

Bei nahem heranzoomen fällt auf:

* die Latexschriften sind beliebig fein
* die Formen sind rasterisiert. Die DPI könnte beim Export noch hochgeschraubt werden.
	* will man das auch noch richtig machen, muss man wirklich in [03 01 03 mitTikz](./03_01_03_mitTikz.markdown) einsteigen


