# praktikum-protokollvorlage-einfach
Vereinfachte LaTeX-Vorlage für die Protokolle der physikalischen Praktika an der Fakultät für Physik am KIT

## Codeschnipsel für die wichtigsten Dinge

### Bilder/Grafik einfügen

```
\begin{figure}[h] 
    \centering
    \includegraphics{include/Foto.png} % Lade die Datei Foto.png aus dem include-Ordner
    \caption{} % Bildunterschrift
    \label{} % Bildbezeichnung, um später darauf zu referenzieren zu können
\end{figure}
```

### Tabellen einfügen

```
\begin{table}[]
    \centering
    \caption{} % Tabellen haben Überschriften!
    \label{} % Tabellenbezeichnung, um später darauf zu referenzieren zu können
    \bigskip % Sorge dafür, dass die Überschrift nicht an der Tabelle klebt
    \begin{tabular}{c|c|c} % Tabelle mit drei Spalten, deren Inhalte mitig zentriert sind
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