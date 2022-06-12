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
pandoc file.md --standalone --template=seminarfach -o outputfile.pdf --pdf-engine=xelatex
```

# Ressourcen

+ [allgemeine Ressourcen zu Pandoc und Markdown](https://baireuther.de/page/markdown/)
+ [Pandoc Installation](https://pandoc.org/installing.html)

# Todo

+ [ ] definition von `documentclass` unnötig machen 
+ [ ] vielleicht generelle einführung in Pandoc
+ [ ] Richtige Zitierweise implementieren siehe [CSL](https://github.com/citation-style-language/styles)
	+ [CSL-Editor](https://editor.citationstyles.org/about/)
	+ [Pandoc-citations](https://pandoc.org/MANUAL.html#citations)
	+ Vorlagen die möglicherweise passen: [1](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Fneuroimaging-clinics-of-north-america), [2](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Fbritish-journal-of-dermatology)
	+ und dann natürlich noch erklären eg. .bib datein etc.
