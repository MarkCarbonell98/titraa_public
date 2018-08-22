# 03 03 Subplots
Created Montag 16 Januar 2017


__Wichtig! Seite zu Ende lesen.__

* die Sache mit der Skalierung beachten
* bei surfplots ⇒ texmemory ist begrenzt. Macht die Plots kleiner wenn möglich


Packages:
	\usepackage{graphicx}
	\usepackage{subcaption}



Beachten für die Ausarbeitung
-----------------------------

* nebeneinander platzierte Plots sollten die gleiche Skalierung der Achsen haben



Subplots in Latex mit \begin{subfigure}
---------------------------------------

### \begin{subfigure} prinzipiell

* die ``subfigure``**-**Umgebung muss ein einer ``figure`` Umgebung stehen
* die ``subfigure``**-**Umgebung benötigt eine Platzierung ``[t]`` ``[b]`` und eine Größe, beispielsweise ``{0.49\textwidth}``
	* wenn man die ``subfigure``**-**Umgebungen nebeneinander platzieren möchte, dürfen sich die Längen nicht zu 1 addieren
* ``\null`` fügt ein unsichtbares zeichen ein


	\begin{figure}[htb]
		\centering
		\null\hfill
		\begin{subfigure}[t]{.525\textwidth}
			\centering
				\includegraphics[width=\textwidth, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_noSizeGaussWin2D.tikz}
			\caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
			\label{subfig:plot_left}
		\end{subfigure}
		\hfill
		\begin{subfigure}[t]{.425\textwidth}
			\centering
			\includegraphics[width=\textwidth, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_noSizeHannWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
	          \label{subfig:plot_right}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    	% Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\caption[Zwei Subplots.]{Zwei Subplots nebeneinander.}
		\label{fig:subplots}
	\end{figure}



### \begin{subfigure}[b] vs \begin{subfigure}[t]
``\begin{subfigure}[t]``
⇒ Die Titel der Plots werden an einer Höhe ausgerichtet
![](./03_03_Subplots/pasted_image016.png)


``\begin{subfigure}[b]``
⇒ Die untere Zeile der Abbildungsbeschriftung wird auf einer Höhe ausgerichtet
![](./03_03_Subplots/pasted_image017.png)


### Zwei Subplots nebeneinander - die Sache mit tikzscale

1. Wir erstellen zwei Plots und exportieren sie mit  ``matlab2tikz``  mit der Option `` 'noSize', true, ...``

	%% tikz export with noSize
	outfname = ['tikz_noSize' figureName '.tikz'];    %% you can choose this freely
	cleanfigure;
	%%Mögliche exportmöglichkeiten:
	% matlab2tikz(outfname,...
	%           ... %'height','6cm','width','62mm', ... %% (a) beides fest setzen.
	% 			... % 'noSize',true, ... %%	(b) komplett dynamisch, schlecht für subplots
	matlab2tikz(outfname,'noSize', true,...
	            'extraAxisOptions', {...
	                'xtick={-1, -0.5, 0, 0.5, 1}',...
	                'xticklabels={$\num{-1}$, $\num{-0,5}$, $\num{0}$, $\num{0,5}$, $\num{1,0}$}',...
	                'ytick={-1, -0.5, 0, 0.5, 1}',...
	                'yticklabels={$\num{-1}$, $\num{-0,5}$, $\num{0}$, $\num{0,5}$, $\num{1,0}$}',...
	                'ztick={-1, -0.5, 0, 0.5, 1}',...
	                'zticklabels={$-1$, $-\frac{1}{2}$, $0$, $\frac{1}{2}$, $1$}',...
	                'font=\footnotesize'},...
	            'parseStrings', false ...
	            );
		

2. Wir möchten die Plots nebeneinander platzieren
	a. dabei sollen beide nicht gleichgroß sein → ``subfigure``-Umgebung unterschiedlich breit
	b. die Plots haben nicht die gleiche Anzahl Datenpunkte
	c. die Plots haben unterschiedlich lange Titel (mehrere Zeilen, ...)
	d. __Das ist quasi der allgemeinste Fall, den man sich vorstellen kann.__
3. Man kann ja mal versuchen, die Plots einfach straight-forward wie vorher mit ``\includegraphics[width=\textwidth, axisratio=1.5]``

einzubinden....
	%% subplots nebeneinander, absolute größenangaben und 'noSize' option
	\begin{figure}[htb]
		\centering
		\null\hfill
		\begin{subfigure}[t]{.525\textwidth}
			\centering
			\includegraphics[width=\textwidth, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_noSizeGaussWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
	          \label{subfig:plot_left}
		\end{subfigure}
		\hfill
		\begin{subfigure}[t]{.425\textwidth}
			\centering
			\includegraphics[width=\textwidth, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_noSizeHannWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
	          \label{subfig:plot_right}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    % Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\caption[Zwei Subplots.]{Mit automatischer Tikzscale-Skalierung}
		\label{fig:subplots}
	\end{figure}


![](./03_03_Subplots/pasted_image011.png)


5. Das geht schief, denn
	a. Die Abbildungen sind nicht gleich groß
	b. die Titel sind nicht an der Oberkante ausgerichtet, wie eigentlich von ``\begin{subfigure}[t]`` erwartet 


### Man könnte ja mal [height=6cm] versuchen ...
Also probieren wir das hier:

* ``\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_noSizeGaussWin2D.tikz}``
* weiterhin ``matlab2tikz``  mit der Option `` 'noSize', true, ... ``also quasi keine Änderungen


	%% subplots nebeneinander, absolute größenangaben und 'noSize' option
	\begin{figure}[htb]
		\centering
		\null\hfill
		\begin{subfigure}[t]{.525\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_noSizeGaussWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
	          \label{subfig:plot_left}
		\end{subfigure}
		\hfill
		\begin{subfigure}[t]{.425\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_noSizeHannWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
	          \label{subfig:plot_right}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    % Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\caption[Zwei Subplots.]
		{Mit automatischer Tikzscale-Skalierung und 'noSize', true | Option in matlab2tikz.
		height=4.8cm, axisratio=1.5.}
		\label{fig:subplots}
	\end{figure}

![](./03_03_Subplots/pasted_image012.png)

Wie man sieht ist die linke Abbildung ziemlich zerschossen worden.

### ... klappt leider nicht, deshalb in matlab2tikz Größe festlegen
__Fazit: __ Man überlegt sich kurz die Größe, die man haben will und stellt das in matlab2tikz ein.

1. Die gesamte Breite der Figure darf nicht größer als __16cm__ sein
	a. die eingestellte relative Größe der ``subfigure``**-**Umgebung muss beachtet werden


oBdA folgendes Zahlenbeispiel:

* linke ``subfigure``**-**Umgebung : 0,525 * 16cm (wegen ``\textwidth``) gibt 8,4cm breite
* rechte ``subfigure``**-**Umgebung: 0,425 * 16cm (wegen`` \textwidth``) gibt 6,8cm breite
* so gesehn sind 7,2cm (frei gewählt) als Breite ok (könnte aber auch ne overfull-box geben, siehe unten)
	* Seitenverhältnis zu 1,5 gewählt ⇒ 4,8 Höhe
* das alles in ``matlab2tikz(outfname,'height','4.8cm', 'width','7.2cm', ... `` 



	matlab2tikz(outfname,...
				... %eine option der beide nächsten
	            'height','4.8cm', 'width','7.2cm', ...  
				... % 'noSize',true, ...		%diese option wenn keine subplots benötigt werden
	            'extraAxisOptions', {...
	                'xtick={-1, -0.5, 0, 0.5, 1}',...
	                'xticklabels={$\num{-1}$, $\num{-0,5}$, $\num{0}$, $\num{0,5}$, $\num{1,0}$}',...
	                'ytick={-1, -0.5, 0, 0.5, 1}',...
	                'yticklabels={$\num{-1}$, $\num{-0,5}$, $\num{0}$, $\num{0,5}$, $\num{1,0}$}',...
	                'ztick={-1, -0.5, 0, 0.5, 1}',...
	                'zticklabels={$-1$, $-\frac{1}{2}$, $0$, $\frac{1}{2}$, $1$}',...
	                'font=\footnotesize'},...
	            'parseStrings', false ...
	            );        


	%% subplots nebeneinander, absolute größenangaben und size in tikz angegeben
	\begin{figure}[hb]
		\centering
		\null\hfill
		\begin{subfigure}[t]{.525\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeGaussWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
	          \label{subfig:plot_left}
		\end{subfigure}
		\hfill
		\begin{subfigure}[t]{.425\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeHannWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
	          \label{subfig:plot_right}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    % Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\caption[Zwei Subplots.]{Ohne automatische Tikzscale-Skalierung und festen Maßen in matlab2tikz}
		\label{fig:subplots}
	\end{figure}


![](./03_03_Subplots/pasted_image013.png)

### Subplots untereinander
Man kann die Subplots untereinander anordnen, indem man eine ``\newline`` zwischen den ``subfigure``**-**Umgebungen und ``\hfill``
einfügt. Man sollte beachten, dass eine leere Zeile gleichbedeutend mit dem ``\newline`` Befehl ist.

Außerdem sollte man unbedingt das Seitenverhältnis der Plots anpassen, da es sonst extrem groß wird. ( ``axisratio = 4 )``

Fügt man also die ``\newline`` vor und nach ``\hfill`` ein passiert folgendes:
![](./03_03_Subplots/pasted_image021.png)

	% subplots untereinander
	\begin{figure}[hbt]
		\centering
		\null\hfill
		\begin{subfigure}[t]{.95\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeGaussWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    % Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\newline	
		\null\hfill
		\begin{subfigure}[t]{.95\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeHannWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    % Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\caption[subplots untereinander]{subplots untereinander}
	\end{figure}


### Grid aus Plots
Völlig analog kann man Raster von Plots einfügen

* es empfiehlt sich wieder, die Größe in matlab2tikz anzugeben
	* ``matlab2tikz(outfname,'height','4.8cm', 'width','7.2cm', ... ``


![](./03_03_Subplots/pasted_image020.png)

	% subplot grid
	\begin{figure}[hbt]
		\centering
		\null\hfill
		\begin{subfigure}[t]{.525\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeGaussWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
		\end{subfigure}
		\hfill
		\begin{subfigure}[t]{.425\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeHannWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    % Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\newline	
		\null\hfill
		\begin{subfigure}[t]{.525\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeHannWin2D.tikz}
	          \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
		\end{subfigure}
		\hfill
		\begin{subfigure}[t]{.425\textwidth}
			\centering
			\includegraphics[height=4.8cm, axisratio=1.5]{bilder/plots/tikz/Subplots/tikz_fixedSizeGaussWin2D.tikz}		
		  \caption{Mit Matlab ersteller 2D-plot. Exportiert mit matlab2tikz und anschließend eingebunden.}
		\end{subfigure}
		\hfill\null % \null fuegt unsichtbares Zeichen ein, damit \hfill funktioniert. 
			    % Zum Verstaendnis einfach mal \null auskommentieren und sehen, was passiert.
		\caption[2 $\times$ 2 Plot-Grid]{2 $\times$ 2 Plot-Grid}
	\end{figure}


Subplots direkt aus Matlab heraus exportieren [geht leider nicht]
-----------------------------------------------------------------
... das geht leider nicht so straight-forward

![](./03_03_Subplots/pasted_image019.png)  ⇒  ![](./03_03_Subplots/pasted_image018.png)


* Die Plots liegen übereinander (man sieht nur den oberen, das ist der zweite plot). Da der außere Bereich *transparent* ist, sind die Titel überlagert.



Subplots referenzieren
----------------------
![](./03_03_Subplots/pasted_image010.png)



Weitere Hinweise
----------------

### Schwarzer Balken → overfull boxes

* ☐ TODO


### Welches Paket wird eigentlich verwendet?
``subcaption``-Paket
Das sollte immer den beiden veralteten Paketen ``subfigure`` und ``subfig`` vorgezogen werden.

