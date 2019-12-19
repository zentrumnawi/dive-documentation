Das *GlossaryEntry* Model definiert einen Eintrag in das Glossar der App, der neben einem erklärenden Text auch optional ein Bild enthalten kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| id | UUIDField(primary_key=True, default=uuid.uuid4, editable=False, unique=True) | UUID eines Eintrags |
| term | CharField(max_length=100) | Begriff, der im Glossar erklärt wird. |
| text | TextField() | Erklärungstext zum Begriff |
| img_url | URLField(blank=True, default="") | URL, unter der ein Bild abgerufen wird. |
| img_alt | CharField(max_length=200, blank=True, default="") | Alternative Textbeschreibung des Bildes |

Das Feld `id` enthält eine eindeutige Eintragskennung. Die Felder `term` und `text` dürfen nicht leer sein. Wird dem Feld `img_url` ein nichtleerer Wert zugewiesen, so darf das Feld `img_alt` auch nicht leer sein.
