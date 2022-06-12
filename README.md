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

### Kompilieren

+ template datei muss in User-Dir/templates sein siehe `pandoc -v`
	+ unter Linux: `~/.local/share/pandoc/templates`
	+ unter Windows: `C:\Users\USERNAME\AppData\Roaming\pandoc`
+ Befehl:

```bash
pandoc file.md --standalone --template=seminarfach -o outputfile.pdf --pdf-engine=xelatex
```

# Todo

+ [] Beispiel Datei
+ [] definition von `documentclass` unnötig machen 
+ [] vielleicht generelle einführung in Pandoc
