Das *GlossaryEntry*-Model definiert einen Eintrag in das Glossar der App, der neben einem erklärenden Text auch optional ein Bild enthalten kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| term | CharField(max_length=100) | Begriff, der im Glossar erklärt wird. |
| text | TextField() | Erklärungstext zum Begriff |
| img | FileField(upload_to="glossary/", null=True) | Eintrag eines möglichen Bildes. |
| img_alt | CharField(max_length=200, blank=True, default="") | Alternative Textbeschreibung des Bildes |

Die Felder `term` und `text` dürfen nicht leer sein, damit kein leerer Abschnitt oder nicht erklärter Begriff im 
Glossar enthalten ist. Wird dem Feld `img_url` ein nichtleerer Wert zugewiesen, so darf das Feld `img_alt` auch 
nicht leer sein.
