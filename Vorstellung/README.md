# Ein einfacher Pandoc/Markdown-Spickzettel

pandoc ist ein Toolpaket zur Konvertierung zwischen Textformaten.
Was ich hier beschreibe, ist nur ein winziger Bruchteil dessen, was man
damit machen kann.

Es ist so einfach wie:

`$ pandoc -s datei.txt -o datei.rtf`

(Ersetzen Sie \"rtf\" durch html usw., um etwas anderes zu erhalten).

Es kann eine Datei konvertieren, die nur aus Tippen besteht, aber wenn
Sie ein wenig einfache Formatierung verwenden, ziemlich genau eine
Version der Markdown-Syntax, können Sie ein schönes RTF mit einigen
nützlichen Zusatzfunktionen (zum Beispiel Kursivschrift) erhalten. Für
eine Überschrift benutzen Sie '#'. 1 # steht für Ebene 1 (Titel).
2 # steht für Ebene 2, usw. Es gibt insgesamt 6 Ebenen.


# Überschrift 1
## Überschrift 2
...
###### Überschrift 6 

---

Die Absatzbildung wird durch Leerzeilen bestimmt, so dass dieser Text in
der RTF-Datei einen Absatz ergibt und\...

Dieser Text\
enthält auch\
einen Absatz\
in der RTF-Datei.

Wenn ich einen Return erzwingen will, beende ich eine Zeile mit einem
Backslash.

Dies funktioniert nicht innerhalb von einfachen Anführungszeichen (siehe unten), die die
wortwörtliche Umgebung darstellen. Wenn ich also zum Beispiel einen
Haufen Zeug wortwörtlich, ohne Zwischenabstände, haben möchte, beende
ich jede Zeile mit einem Backslash *außerhalb der* Anführungszeichen:

`Zeile 1''`\
`Zeile 2''`\
`` `Zeile 3` ``

wird geben

`Zeile 1`\
`Zeile 2`\
`Zeile 3`

## Schriftarten formatieren

Das Wort ist das Zeichen, das zur Abgrenzung des geänderten Textes
verwendet wird. Der Code wird ebenfalls wörtlich angegeben.

*Unterstrich* `_Unterstrich_`

*Dollar* (mathematisch, was sich nicht in RTF übersetzen lässt)
`$dollar$`

^caret^ (hochgestellt) \^caret\^

~tilde~ (tiefgestellt) `~tilde~`

~~2 tildes~~ `~~tilde~~`

**2 Unterstriche** `__2 Unterstriche__`

**2 Sternchen** `**2 Sternchen**`

***3 Sternchen*** `***3 Sternchen***`

`zurück ticken ``` `zurück ticken` ``

Beachten Sie, dass bei der Verwendung von Back Ticks (wortwörtlich) die
Verschachtelung der Anweisungen von Bedeutung ist

`***Rückwärtshaken außerhalb von 3 Sternchen***`

`3 Sternchen außerhalb des hinteren Häkchens`

`2 Sternchen außerhalb des hinteren Häkchens`

`1 Sternchen außerhalb des hinteren Häkchens`

## Andere Dinge

(Anmerkung: Die obige Zeile (\"Sonstiges\") wurde in der unmittelbar
folgenden Zeile mit Bindestrichen unterstrichen).

Nonbreaking Space - einem Leerzeichen wird ein Backslash vorangestellt:
\'\\⌴\' (ich verwende ⌴ für ein Leerzeichen)

> Anführungszeichen: \> (größer als leitet ein um 1 Tabulator
> eingerücktes Anführungszeichen ein)
>
> Blockzitat, wieder: \>\> gleich, größerer Einzug

So zum Beispiel

    >Dieser Text würde als Blockzitat erscheinen, das um 1 Tabulator eingerückt ist.

# H1 (1 Raute, #)

Also schreiben:

    # Hier ist meine Überschrift 1

## H2 (2 Hashes, ##)

    ## Hier ist meine Überschrift 2

### H3 (3 Hashes, ###)

    ### Hier ist meine Überschrift 3

-   Aufzählungspunkt (+ am Anfang der Zeile, dann Leerzeichen)
-   Aufzählungspunkt (- (Bindestrich) am Anfang der Zeile, dann
    Leerzeichen)
-   Aufzählungspunkt (\* am Anfang der Zeile, dann Leerzeichen)

1.  Nummerierte Liste
2.  Nummerierte Liste noch
3.  Erneut nummerierte Liste

(einfach eine Zeile mit einer Nummer und einem Stopp beginnen)

\- 2 Bindestriche für en-Regel

\- 3 Bindestriche für em-Regel

## Metadaten

Bei einigen Formaten (z. B. HTML) müssen Metadaten angegeben werden. Am
einfachsten ist es, wenn man

`% Titel`\
`% Autor(en)`\
`% Datum`

ganz oben in der Datei (ersetzen Sie \"Titel\", \"Autor\" und \"Datum\"
durch Ihren eigenen Text).


---

TODO:

  
+ [ ] Fußnoten und Bilder Verlinkung erklären
+ [ ] Pandoc Templates erklären
+ [ ] PDF-Engines Installerprobleme erklären
 
 
