# Vereinfachte Pratikumsprotokollvorlage
Dies ist die vereinfachte LaTeX-Vorlage für die Protokolle der physikalischen Praktika an der Fakultät für Physik am 
KIT. Wir haben festgestellt, dass die eigentlich [Vorlage](https://github.com/fsphys/praktikum-protokollvorlage-latex)
vor allem für Neulinge nicht wirklich verständlich ist und bieten nun auch diese Vorlage an.

## Kurzanleitung
Hier ist eine einfache Anleitung, wie du mit dieser Vorlage anfängst.

1. Richte dir deine Arbeitsumgebung ein. Dafür kannst du gerne einen lokalen Compiler verwenden, wir empfehlen für 
 Beginner aber immer [Overleaf](https://www.overleaf.com/).
   1. Gehe auf den **Log In**-Button.
   2. Scrolle runter und klicke auf **Log in through your institution**.
   3. Tippe in das Eingabefeld deine KIT-Adresse mit dem Format `uXXXX@student.kit.edu` ein.
   4. Melde dich, wie von zum Beispiel ILIAS gewohnt, mit deinem KIT-Account an.
   5. Bewundere die Übersichtseite von Overleaf.
2. Lade dir das Projekt als ZIP-Datei über
 [**diesen Link**](https://github.com/fsphys/praktikum-protokollvorlage-einfach/archive/refs/heads/main.zip) herunter.
3. Falls du lokal arbeitest, so entpacke die Datei und kopier die Dateistruktur in deine Arbeitsstruktur, um diese dann
 mit einem Editor deiner Wahl zu bearbeiten. Falls du **Overleaf** verwendest, so musst du auf **New project** klicken,
 dort **Upload project** auswählen und die soeben heruntergeladene ZIP-Datei dort hochladen.
4. Nun bist du soweit und kannst mit der Bearbeitung der Dateien anfangen. Es ist sinnvoll folgende Änderungen direkt am
 Anfang vorzunehmen. Diese sind
   1. Stelle sicher, dass du die richtige Deckblattdatei für ein Praktikum lädst.
   2. Fülle die Daten zu deinem Praktikum in der entsprechenden Deckblattdatei aus.
   3. Ersetzte die Demo-PDF-Dateien mit den Dateien, die du für deinen Versuch benötigst.
5. Viel Erfolg mit der Vorlage!

## Codeschnipsel für die wichtigsten Dinge

Hier findest du eine Auflistung an wichtigen Beispielen, die für LaTeX-Neulinge sehr hilfreich sein können.

### Bilder/Grafik einfügen

```
\begin{figure}[h] 
    \centering % Zentriere das Bild horizontal
    \includegraphics{include/Foto.png} % Lade die Datei Foto.png aus dem include-Ordner
    \caption{} % Bildunterschrift
    \label{} % Bildbezeichnung, um später darauf zu referenzieren zu können
\end{figure}
```

Unterstützte Dateiformate: `*.png`, `*.jpg`, `*.jpeg`, `*.pdf`

Solltest du andere Rastergrafikformate verwenden (`*.bmp`, ...), so empfiehlt sich die Konvertierung in eine `*.png`
bzw. `*.jpeg/*.jpg` mit Standardprogrammen wie Microsoft Paint, GIMP oder weiteren Tools. Solltest du mit `*.eps` oder
`*.svg` Formaten hantieren, so empfiehlt sich hier die verlustfreie Konvertierung in `*.pdf`-Dateien mit Hilfe
von Tools wie Inkscape, LibreOffice oder weiteren.

### Tabellen einfügen

Falls du Tabellen manuel schreibst, so kannst du dies wie folgt machen:

```
\begin{table}[]
    \centering
    \caption{} % Tabellen haben Überschriften!
    \label{} % Tabellenbezeichnung, um später darauf zu referenzieren zu können
    \bigskip % Sorge dafür, dass die Überschrift nicht an der Tabelle klebt
    \begin{tabular}{ccc} % Tabelle mit drei Spalten ohne Trennstriche, deren Inhalte mitig zentriert sind
        \toprule
        Text & Text & Text\\ % Spaltenbezeichungen
        \midrule
        Text & Text & Text\\ % Tabelleninhalt
        Text & Text & Text\\
        Text & Text & Text\\
        \bottomrule
    \end{tabular}
\end{table}
```

Solltest du die Daten bereits in einer `*.csv`-Datei haben, so kannst du diese auch einfach mithilfe von diesem 
Code-Schnipsel aus Dateien auslesen und dir anzeigen lassen.

```
\begin{table}[]
    \centering
    \caption{} % Tabellenüberschrift
    \label{} % Label der Tabelle fürs referenzieren
    \bigskip % Stelle sicher, dass die Überschrift nicht an der Tabelle klebt
    \pgfplotstabletypeset[
        columns={Nr,Length(um),Depth(nm)}, % Spalten aus der CSV-Datei, die importiert werden sollen
        % Die folgenden Parameter geben für jede Spalte an:
        % column name={Bezeichung der Spalte}
        % precision=Anzahl der Stellen, die Zahlen in der Spalte haben sollen
        % fixed zerofill -> Fülle mit Nullen auf, sollte der Wert nicht die Länge der precision haben
        % fixed -> Runde die Zahlen auf die precision
        % column type = {r} -> Wie ist die Spalte ausgerichtet (r: rechtsbündig, l: linksbündig, c: zentriert)
        display columns/0/.style={column name={Nr.}, precision=0, fixed zerofill, column type = {r}},
        display columns/1/.style={column name={Länge $l$ ($\si{\micro\meter}$)}, precision=1, fixed, fixed zerofill, column type = {r}},
        display columns/2/.style={column name={Tiefe $t$ ($\si{nm}$)}, precision=0, fixed zerofill, column type = {r}},
        ]{Daten.csv} % Lese die Daten aus der Daten.csv-Datei aus
\end{table}
```

### Referenzierung

Die Referenzierung von Objekten ist recht einfach. Dafür muss an der Stelle, die referenziert werden soll, ein
`\label{Beispielname}` erstellt werden, um dann mit `\ref{Beispielname}` darauf verweisen zu können. Dabei gilt,
dass jeder Name nur einmal mit dem `\label`-Befehl definiert werden darf, denn sonst kann LaTeX die Referenz nicht mehr 
eindeutig identifizieren.

```
Dies ist ein Beispieltext, der auf ein Beispielbild in Abbildung \ref{Beispielname} zeigt.
```

### Formeln

```
\begin{equation}
    n = \frac{2 \cdot L}{\lambda},
\end{equation}
```

```
\begin{equation}
    m_\text{e} = m \pm \sigma_\text{stat} \pm \sigma_\text{sys}
\end{equation}
```

Eine relativ ausführliche Übersicht der verfügbaren Zeichen kann
[hier](https://de.wikipedia.org/wiki/Liste_mathematischer_Symbole) gefunden werden.

### Wertangabe

Entweder:
```
\begin{equation}
    m_\text{e} = \SI{9.1093837015e-31}{\kilo\gram}
\end{equation}
```

oder
```
\begin{equation}
    m_\text{e} = 9.1093837015 \cdot 10^{-31}~\si{kg}
\end{equation}
```

#### Fehler-Rechnung Wertangabe:
Die Angabe von Ergebnissen der Fehlerrechnung erfolgt nach dem Schema:
> Ergebnis = Messwert +/- statistischer Fehler +/- systematischer Fehler

Dies ist hier beispielhaft dargestellt
```
\begin{equation}
    m_\text{e} = 9.1093837015 \cdot 10^{-31}~\si{kg} \pm 0.01~\si{kg} \pm 20.01~\si{kg} 
\end{equation}
```

### Fussnoten

```
\footnote{Hier steht etwas ganz wichtiges: $\pi=e=3$}
```

### Listen

#### Umnummerierte Listen

```
\begin{itemize} 
    \item Ein Stichpunkt 
    \item Noch ein Stichpunkt 
\end{itemize}
```

#### Nummerierte Listen
```
\begin{enumerate} 
    \item Ein Stichpunkt
    \item Noch ein Stichpunkt 
\end{enumerate}
```

## Ich habe einen Fehler entdeckt. Was nun?

Falls du einen Fehler entdeckt hast, dann teil ihn uns Bitte mit. Dies kannst du entweder mit einem Eintrag bei den
[Projekt-Issues](https://github.com/fsphys/praktikum-protokollvorlage-einfach/issues) machen oder einfach eine E-Mail
an latexvorlage@fachschaft.physik.kit.edu schreiben.

Solltest du andere Verbesserungsvorschläge haben, so akzeptieren wir diese gerne als Pull-Requests. Gerne kannst du uns 
die Vorschläge auch einfach per E-Mail an latexvorlage@fachschaft.physik.kit.edu zukommen lassen. 

## License

This project is licensed under the `The MIT License (MIT)`. For more information consulte the [License](LICENSE)-file. 