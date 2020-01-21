Das *GlossaryEntry*-Model definiert einen Eintrag in das Glossar der App, der neben einem erklärenden Text
auch optional ein Bild enthalten kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| term | CharField(max_length=100) | Begriff, der im Glossar erklärt wird. |
| text | TextField() | Erklärungstext zum Begriff |
| img | ImageField(upload_to="glossary/images/", null=True, blank=True) | Optionales Bild |
| img_alt | CharField(max_length=200, blank=True, default="", validators=[validate_img_is_not_empty]) | Alternative Textbeschreibung des Bildes |
| links | ManyToManyField("self", symmetrical=False, blank=True) | Links auf andere Glossareinträge |

Die Felder `term` und `text` dürfen nicht leer sein, damit kein leerer Abschnitt oder nicht erklärter Begriff
im Glossar enthalten ist. Das Feld `img` speichert einen Verweis auf ein Bild in Form eines relativen
Verzeichnispfades als String, wobei das Bild selbst hochgeladen und im `glossary/images/`-Verzeichnis
gespeichert wird. Wird ein Bild verwendet, so darf das Feld `img_alt` auch nicht leer sein. Das Feld `links`
speichert, sofern erforderlich, die Primärschlüssel von anderen Glossareinträgen, zu denen dann verwiesen
werden kann.

Da kein Feld als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung enthält.
