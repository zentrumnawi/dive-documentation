Das *GlossaryEntry*-Model definiert einen Eintrag in das Glossar der App, der neben einem erklärenden Text auch optional ein
Bild enthalten kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| term | CharField(max_length=100) | Begriff, der im Glossar erklärt wird. |
| text | TextField() | Erklärungstext zum Begriff |
| img | ImageField(upload_to="glossary/", null=True, blank=True) | Verweis auf ein optionales Bild |
| img_alt | CharField(max_length=200, blank=True, default="") | Alternative Textbeschreibung des Bildes |

Die Felder `term` und `text` dürfen nicht leer sein, damit kein leerer Abschnitt oder nicht erklärter Begriff im Glossar
enthalten ist. Im Feld `img` wird ein Verweis auf ein Bild in Form eines relativen Verzeichnispfades als String gespeichert,
wobei das Feld auch erlaubt, dass ein Bild hochgeladen werden kann, das dann im `glossary`-Verzeichnis gespeichert wird. Wird
dem Feld ein nichtleerer Wert zugewiesen, so darf das Feld `img_alt` auch nicht leer sein.

Da kein Feld als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen eindeutigen Integer als
Kennung enthält.
