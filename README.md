# Templates für die Seminarfacharbeit an der TGS-Weimar

## Pandoc Template

Das Template [seminarfach.latex](https://gitlab.com/october32551/tgsw_semi/-/blob/main/templates/seminarfach.latex) ist eine Modifikation des [default Pandoc Templates](https://github.com/jgm/pandoc/blob/master/data/templates/default.latex).

### Variablen

Die folgenden Variablen müssen in dem [Yaml Metadata Block](https://pandoc.org/MANUAL.html#extension-yaml_metadata_block) der Markdown Datei angegeben werden um das Titelblatt und die Kopfzeile richtig zu generieren.

#### allgemein Variablen

+ `documentclass`
	+ eg. `documentclass: article`
+ `mainfont`
	+ eg. `mainfont: Carlito`
+ `titel`
	+ eg. `titel: Ein sehr langer Titel der meine Seminarfacharbeit beschreibt`
+ `kurztitel` für für Kopfzeile
	+ falls `titel` zu lang für die Kopfzeile ist, kann **auch** ein kurztitel definiert werden
	+ eg. `kurztitel: Mein Thema`
+ `student`
	+ wenn mehrere Angegeben werden sollten diese schon Alphabetisch sortiert angegeben werden
	+ eg.:

```yaml
student:
- nachname: Mustermann
  name: Max
  stammkurs: 11 1
- nachname: Müller
  name: Marie
  stammkurs: 12 3
```

+ `nur-nachname`
	+ kann zu `nur-nachname: true` gesetzt werden um nur die Nachnamen in der Kopfzeile zu setzen

#### Deckblatt

Falls ein Deckblatt generiert werden soll müssen diese Variablen gesetzt werden und `deckblatt: true` hinzugefühgt werden.

+ `schulname`
	+ eg. `schulname: Staatliche Gemeinschaftsschule Weimar`
+ `seminarfachlehrer-in`, `seminarfachlehrerin` oder `seminarfachlehrer`
	+ eg. `seminarfachlehrer: Max Mustermann`
	+ `Seminarfachlehrer-in` für SeminarfachlehrerIn
+ `fachbetreuer-in`, `fachbetreuerin` oder `fachbetreuer`
	+ eg. `fachbetreuerin: Martina Mustermann`

Um eine eigenes Latex-Deckblatt zu benutzen muss `deckblatt-datei: Pfad-zur-datei` angegeben werden, z.B. `deckblatt-datei: ./deckblatt.tex`

### Zitieren

Um Zitate in den Fußnoten nach den Vorgaben zu formatieren, kann diese [CSL-Datei](csl/tgs-weimar-seminarfach.csl) benutzt werden. Dazu muss diese im Header angegeben werden.

```yaml
csl: ./tgs-weimar-seminarfach.csl
```

Damit Es überhaupt etwas zu Zitieren gibt, wird eine Bib-Latex Datei benötigt. Diese kann einfach aus [Zotero](https://www.zotero.org/) mit dem [Better Bibtex Addon](https://retorque.re/zotero-better-bibtex/installation/) exportiert werden. Dabei müssen sogenannte Citation-Keys für jeden Eintrag (Quelle) [gesetzt werden](https://alix-lahuec.gitbook.io/zotero-roam/getting-started/prereqs#setup-checklist). Dann können die Quellen in eine Bib-Latex Datei exportiert werden, in dem beim Rechtsklick auf die Sammlung oder Bibliothek exportiern gewählt wird und im erscheinenden Menü das Format zu Better Biblatex gesetzt wird und und besten auch noch "Halte aktuell" ausgewählt wird. In der Markdown-Datei kann dann so die Quelle angegeben werden:

```md
Ich zitiere: „Sein oder Nichtsein, das ist hier die Frage“[@citationkey].
```

Und im Header muss der Pfad zu `.bib` Datei angegeben werden z.B.:

```yaml
bibliography: ./meine_bibliografie
```

(Unter Windows werden Pfade etwas anders mit einem Backslash (` \ `) angegeben)

### Beispiele

#### Yaml Kopf

```yaml
---
documentclass: article
titel: A very long title about stuff that is very interessting
kurztitel: A title
mainfont: Carlito
deckblatt: true
schulname: Schule Niemandsland
seminarfachlehrer-in: Karl Marx
fachbetreuer: Albert Einstein
student:
- nachname: Erbse
  name: Markus
  stammkurs: 21 1
- nachname: Fuchs
  name: Elise
  stammkurs: 12 7
- nachname: Gurke
  name: Angela
  stammkurs: 14 5
nur-nachname: true
datum: 21. Dezember 1999
csl: ./tgs-weimar-seminarfach.csl
bibliography: ./meine_bibliografie.bib
---
```

#### Dokument

+ [Quell-Markdown](Beispiele/example.md)
+ [Entstandene PDF-Datei](Beispiele/example.pdf)

### Kompilieren

+ template datei muss in User-Dir/templates sein siehe `pandoc -v`
	+ unter Linux: `~/.local/share/pandoc/templates`
	+ unter Windows: `C:\Users\USERNAME\AppData\Roaming\pandoc`
+ Befehl:

```bash
pandoc file.md --standalone --template=seminarfach -o outputfile.pdf --pdf-engine=xelatex -C
```

# Ressourcen

+ [allgemeine Ressourcen zu Pandoc und Markdown](https://baireuther.de/page/markdown/)
+ [Pandoc Installation](https://pandoc.org/installing.html)

# Todo

+ [ ] definition von `documentclass` unnötig machen 
+ [ ] vielleicht generelle einführung in Pandoc
+ [x] Richtige Zitierweise implementieren siehe [CSL](https://github.com/citation-style-language/styles)
	+ [CSL-Editor](https://editor.citationstyles.org/about/)
	+ [Pandoc-citations](https://pandoc.org/MANUAL.html#citations)
	+ Vorlagen die möglicherweise passen: [1](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Fneuroimaging-clinics-of-north-america), [2](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Fbritish-journal-of-dermatology)
	+ und dann natürlich noch erklären eg. .bib datein etc.
+ [ ] Wenn Dokumentation etc. zu viel wird zu wiki umsteigen
