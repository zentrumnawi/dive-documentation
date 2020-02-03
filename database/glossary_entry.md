Das *GlossaryEntry*-Model definiert einen Eintrag in das Glossar der App, der neben einem erklärenden Text
auch ein Bild enthalten kann.

| Feldname | Feldtyp | Nutzung |
| :--- | :--- | :--- |
| term | CharField(max_length=100) | Begriff |
| text | TextField() | Erklärungstext zum Begriff |
| img | ImageField(upload_to="glossary/", null=True, blank=True) | Bild |
| img_alt | CharField(max_length=200, default="", blank=True, validators=[validate_img_is_not_empty]) | Alternative Textbeschreibung des Bildes |
| link_children | ManyToManyField("self", blank=True, related_name="link_parents", symmetrical=False, db_Index=False) | Kennungen von anderen Einträgen |

In den Feldern `term` und `text` werden ein Begriff und der dazugehörige Erklärungstext gespeichert. Um
sicherzustellen, dass kein inhaltsloser Eintrag erstellt wird, dürfen beide Felder nicht leer sein. Soll der
Eintrag ein Bild enthalten, so wird im Feld `img` beim Hochladen des Bildes der Verweis auf das Bild in Form
eines relativen Verzeichnispfades mit „glossary/“ als Unterverzeichnis als String gespeichert. Falls ein Bild
verwendet wird, muss zusätzlich im Feld `img_alt` angegeben werden, was im Bild zum Ausdruck kommt. Das Feld
`link_children` speichert die Primärschlüssel von anderen Einträgen, zu denen aus einem Objekt heraus
verwiesen wird. 

Da kein Feld im Model als Primärschlüssel ausgewiesen ist, fügt Django automatisch ein Feld hinzu, das einen
eindeutigen Integer als Kennung für ein Objekt enthält.
