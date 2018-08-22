# 03 02 Matlabplots
Created Freitag 02 Dezember 2016


Die bevorzugte Weise einen plot aus Matlab einzubinden ist durch tikz.
Auch wenn tikz gefürchtet ist, ist der Export eines Plots und das Einbinden ein Kinderspiel.

READ THIS FIRST
---------------

__Zuerst das hier lesen__ 


Windows only: Matlabplot -> Plot2Latex -> Inkscape -> Latex
-----------------------------------------------------------
Getestet unter: Windows 10 - Matlab R16a - Juli 2016

### Anleitung

1. Plot2Latex herunterladen:  <https://www.mathworks.com/matlabcentral/fileexchange/52700-plot2latex>
2. Inkscape installieren
3. Pfad zu Inkscape anpassen
	a. Datei ``Plot2Latex.m``  Zeile 110

   ![](./03_02_Matlabplots/pasted_image001.png)
	C:\Program Files\Inkscape\inkscape.exe


5. neuen Ordner erstellen.
6. Greeks.m und ChangeInterpreter.m in den neuen Ordner kopieren

![](./03_02_Matlabplots/pasted_image.png)


5. einen Plot erstellen und die titles und Achsenbeschriftungen mit Latexcode versehen ($ $ beachten). 
	a. um deutsche Kommas in den Dezimalzahlen zu erhalten, muss der Befehl ``$\num{3}$`` verwendet werden.
	b. Anschließend die Größe des Plots festlegen und Plot2Latex ausführen.  Siehe Beispielcode für mehr Infos. Dies erstellt die folgenden Dateien.

![](./03_02_Matlabplots/pasted_image012.png)
Das Matlab skript lautet
	%%plot2Latex example
	%% prepare Data
	t = linspace(0,1,100);
	s = sin(2*pi()*t);
	fname = 'SinusWave'
	
	
	%% do the plotting
	h = figure('Name', fname); clf;
		%whitebg(f1,'k')	%%set background color black
	    plot(t,s,'*-c');
	    xlim([0,1])
	    ylim([-1,1])
	    legend('$\cos(t)$', 'Location', 'southwest'),
	    ylabel('Magnitude in $\mathrm{m}$')
	    xlabel('$t$ in $\mathrm{s}$')
	    title('$\sin(\omega t)$')
	% Specify width and height of figure and the fontsize. They should correspond 
	% more or less with size in latex.
	h.Units = 'centimeters'; % set figure position to cm
	% h.Position(2) = [h.Position(2)-8.5]; % set figure position before resize
	h.Position([3:4]) = [16,10]; % resize figure  [width,height]
	set(findall(h,'-property','FontSize'),'FontSize',10); % change font size
	ChangeInterpreter(gcf,'Latex');
	
	%% Run the Plot2LaTeX script
	Plot2LaTeX( h, fname )
	
	%% Now run the latex file (___.tex) to generate document


7. Im ___.pdf_tex die Pfade zur _.pdf__ Datei anpassen
	a. Da in der ``___.pdf_tex`` Datei der Befehl ``\includegraphics`` benutzt wird, muss hier die Einstellungen aus der **erweiterungen.tex** beachtet werden. Ist der Stammordner für Bilder der "bilder" Ordner (Standardeinstellung beim Auschecken der Vorlage),  muss der Pfad hier relativ zum Bilder Ordner angegeben werden.
8. Die Datei im Latex-Dokument einbinden

	\begin{figure}[h!]
	  \centering
		  \def\svgwidth{\textwidth}
			\input{bilder/figures/SinusWave.pdf_tex}	%% da hier nur input verwener wird
		  \caption{Eine mit Plot2Latex erstellte Abbildung}
	  \label{fig:SinusWave}
	\end{figure}


### Problem, dass nicht die ganze Seitenbreite ausgefüllt wurde
Möchte man nicht **tikz **verwenden (kommt später) und trotzdem die ganze Seitenbreite ausfüllen, kann man die erzeugte **.svg** Datei in Inkscape öffnen und bearbeiten.

![](./03_02_Matlabplots/pasted_image025.png)


* Rechtsklick auf die Grafik ⇒ Gruppierung aufheben
* irgendwo hinklicken. am Rand klicken und den Transparenten Rahmen verändern.

![](./03_02_Matlabplots/pasted_image026.png)

* Dann wieder Datei ⇒ Dokumenteinstellungen (STRG+SHIFT+D)
* während der Rahmen ausgewählt ist: ⇒ Benutzerdefiniert ⇒ Seite in Auswahl einpassen

![](./03_02_Matlabplots/pasted_image027.png)


* Dann Datei ⇒ Speichern Unter ⇒ PDF Format auswählen
	* auch hier wieder PDF+Latex wählen
	* hohe DPI auswählen (schadet nix, 600 is gut)


![](./03_02_Matlabplots/pasted_image028.png)


### Page group warning unterdrücken
<http://tex.stackexchange.com/questions/76273/multiple-pdfs-with-page-group-included-in-a-single-page-warning>
<http://tex.stackexchange.com/questions/183149/cant-silence-a-pdftex-pdf-inclusion-multiple-pdfs-with-page-group-error>
	%% suppress the page group warning that spams your output !!BE CAREFUL!!
	\pdfsuppresswarningpagegroup = 1	%%suppress pagegroup proble



alle Platformen: Matlabplot -> Matlab 2 tikz -> Latex
-----------------------------------------------------

### Anleitung
auch wenn tikz sehr kompliziert ist, ist die Verwendung von Matlab 2 tikz unglaublich einfach. Außerdem werden auch deutsche Kommas in Dezimalzahlen unterstützt.

1. Matlab 2 tikz herunterladen und in den Matlab pfad einfügen <https://github.com/matlab2tikz/matlab2tikz>
2. Einen Matlab plot erstellen. Verwende Latexcode in den Beschriftungen.

	%%plot2Latex example
	%% prepare Data
	t = linspace(0,1,100);
	s = sin(2*pi()*t);
	figureName = 'SinusWave';
	
	%% do the plotting
	h = figure('Name', figureName); clf;
	    plot(t,s,'*-c');
	    xlim([0,1])
	    ylim([-1,1])
	    legend('$\sin(t)$ over $1$ period', 'Location', 'southwest'),
	    ylabel('Magnitude in $\mathrm{m}$')
	    xlabel('$t$ in $\mathrm{s}$')
	    title('$\sin(\omega t)$')
	

3. exportiere die Datei mit **matlab2tikz (es wurden zeilen zum code hinzugefügt).**

	%% This example shows how to properly prepare a plot using tikz
	% it works on all platform. Make sure you have a full tex distribution
	% installed.
	%% prepare Data
	t = linspace(0,1,100);
	s = sin(2*pi()*t);
	figureName = 'SinusWave';
	
	%% do the plotting
	h = figure('Name', figureName); clf;
	    plot(t,s,'*-c');
	    xlim([0,1])
	    ylim([-1,1])
	    legend('$\sin(\omega t)$', 'Location', 'southwest'),
	    ylabel('Magnitude in $\mathrm{m}$')
	    xlabel('$t$ in $\mathrm{s}$')
	    title('$\sin(t)$ over $1$ period')
	
	    
	%% tikz    
	outfname = [figureName '.tikz'];    %% you can choose this freely
	cleanfigure;
	matlab2tikz(outfname,...
				... %eine option der beide nächsten
				%'height','4cm','width','62mm', ... %diese option für für exakte ausrichtung bei subplots
				'noSize',true ...		%diese option wenn keine subplots benötigt werden
				...			
	            'extraAxisOptions', {...
	                ... %% y axis
	                'yticklabel style={/pgf/number format/use comma,/pgf/number format/fixed}',...  %% use comma for decimal seperation
	                'scaled y ticks = false',...
	                'ytick={-1, -0.5, 0, 0.5, 1}', ...
	                'yticklabels={$\num{-1}$, $\num{-0.5}$, $\num{0}$, $\num{0.5}$, $\num{1}$}',  ...                    ... %% x axis
	                'xticklabel style={/pgf/number format/use comma,/pgf/number format/fixed}',...  %% use comma for decimal seperation
	                'scaled x ticks = false',...
	                'xtick={0, 0.25, 0.50, 0.75, 1} ',...                    
	                'xticklabels={$0$, $\frac{\pi}{2}$, $\pi$, $\frac{3\pi}{2}$, $2\pi$}',...
	                ...
	                'font=\footnotesize'},...
	            'parseStrings', false ...
	            );



5. Tikz Datei in Latex einbinden
	a. richtige Packages im **diplom.tex** einbinden
6. evtl nicht mehr nötig, da präambel aktualisiert

	%% für tikz
	%% ------------------
	%% TikZ
	\usepackage{tikz}
	\usepackage{tikzscale}
	
	%%accelerated compilation
	% \usetikzlibrary{external}
	% \tikzexternalize[prefix=TikZ2pdf/]
	%% PGF-Plots
	\usepackage{pgfplots}
	\pgfplotsset{compat=newest}
	%% ------------------
			 

c. Binde die .tikz Datei in Latex ein. Es wird der \includegraphics Befehl verwendet, beachte also wieder die Ordnerstruktur. Die Endung **.tikz** wird ebenfalls nicht benötigt

	\begin{figure}[h!]
	  \centering
	    \includegraphics[width=\textwidth, axisratio=2]{SinusWaveExamples/SinusWave}
	  \caption{Matlab - TIKZ}
	  \label{fig:matlabTikz}
	\end{figure}
	

### Beschleunigung mit externilze bibliothek von Tikz
Durch Nutzen der Pakete **tikzexternalize** kann der Erstellungsvorgang deutlich beschleunigt werden. **Dies löst aber nicht das Speicherplatzproblem**.
	%% TikZ
	\usepackage{tikz}
	\usepackage{tikzscale}
	
	%%accelerated compilation
	\usetikzlibrary{external}
	\tikzexternalize[prefix=TikZ2pdf/]
	%% PGF-Plots
	\usepackage{pgfplots}
	\pgfplotsset{compat=newest}
	%% ------------------


Um die externalize Funktion zu nutzen, muss der **Shell-escape in der Latex-IDE** aktiviert werden. Dies geht meist, indem die Option --shell-escape zu pdflatex hinzugefügt wird.
Siehe auch für genauere Anleitungen
TiTrAa_IIIT:Handout:01_LatexEditoren:TexStudio
TiTrAa_IIIT:Handout:01_LatexEditoren:TeXnicCenter
TiTrAa_IIIT:Handout:01_LatexEditoren:KILE


### [EXPERIMENTELL] Problem mit zu vielen Datenpunkten (Surfplots) - tex memory exceeded

__Achtung!__ Dieser Teil ist immernoch in Arbeit.

Bei zu vielen Stützpunkten geht pdflatex der speicher aus. Man kann sich noch ein bischen abhilfe schaffen, indem man die tikzbilder mit Lualatex einbindet.
**Das compilieren dauert trotzdem sehr sehr lange. Also umbedingt externalize verwenden, dann dauert es nur 1 mal sehr lange.**

	%% TikZ	
	\usepackage{tikz}
	\usepackage{pgfplots}
	\usepackage{tikzscale}
	\usetikzlibrary{plotmarks}
	
	%% dont change this order
	\usetikzlibrary{external}
	\tikzexternalize[prefix=tikz/]
	
	
	%% PGF-Plots
	\pgfplotsset{compat=newest}
	
	%% ------- this is only working on some pcs
	%% ------- usually makes problems with subplots on linux and mac
	%% ------- try uncommenting this if things get weird
	\usepackage{luatex85}	
	\tikzset{external/system call={lualatex
	\tikzexternalcheckshellescape -halt-on-error -interaction=batchmode
	-jobname "\image" "\texsource"}}


Einbinden weiterhin ganz normal a la

	\begin{figure}[h]
		\centering
		\includegraphics[width=\textwidth,height=0.6\textwidth]{tikz_SurfPlot_hiRes}
		\caption[Matlab2tikz mit suf-Plots]
		{Mit Matlab ersteller surf-Plot. Exportiert mit matlab2tikz und anschließend eingebunden. Die Anzahl Stützstellen beträgt 80 pro Dimension.
		Wegen der großen Menge an Stützpunkten sollte Lualatex verwender wernden. Um längere Compilierzeit nur bei Änderungen in Kauf zu nehmen sollte man externalize verwenden.}
	\end{figure}


__Obergrenze: 50x50 Datenpunkte für surfplots__


### Weitere Fehlermeldungen

##### I can't write on file '....'
![](./03_02_Matlabplots/pasted_image029.png)

**Lösung**
Nachschauen, ob bei tikzexternalize ein prefix eingestellt wurde. Dieser Ordner wird **NICHT **automatisch erstellt und muss daher selbst erstellt werden.
	\tikzexternalize[prefix=tikz/]

![](./03_02_Matlabplots/pasted_image030.png)

Jetzt ist alles wieder gut




plot2latex vs matlab2tikz
-------------------------

![](./03_02_Matlabplots/pasted_Image1.png) ![](./03_02_Matlabplots/pasted_Image0.png)
Links plot2latex - rechts matlab2tikz

Auch wenn der Unterschied minimal ist, ist tikz zu empfehlen → einfacher (in der Regel) und *eleganter*.



![](./03_02_Matlabplots/pasted_Image3.png)  ![](./03_02_Matlabplots/pasted_Image2.png)
Links plot2latex - rechts matlab2tikz

Aufgrund der Speicherbegrenzung von tikz kann man schon mal auf plot2latex zurückgreifen, wenn man umbedingt die Feinheit braucht.
Ansonsten gilt hier auch wieder: tikz ist einfach einfacher.

